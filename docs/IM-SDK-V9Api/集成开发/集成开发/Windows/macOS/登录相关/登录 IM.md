
完成 NIM SDK 的初始化之后，用户需要先调用 SDK 的登录接口登录 IM。登录成功后，用户才能正常调用消息和会话等其他 SDK 接口。

本文介绍账号集成与登录的技术原理、实现 IM 登录的流程、IM 登录状态转换流程，以及[相关常见问题](#常见问题)。


## 技术原理


<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/f7d332058c2fed770bc0691fb3a2dd18/账号集成与登录原理新图.png" />



IM 的登录与账号集成密切相关。上图展示了应用集成 NIM SDK 后，从账号集成到登录 IM 成功的主要流程：


1. 用户在应用客户端注册用户账号时，由应用服务端向云信服务端发起[创建 IM 帐号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server)的请求。
2. IM 帐号创建成功后，云信服务端会返回该 IM 帐号(即`accid)`和`token`等信息。此时，应用服务端需要负责保存`accid`和`token`的映射关系。
3. 应用客户端发起登录请求时，先走应用自有的登录验证逻辑，如帐号和密码的验证。
4. 验证成功后，应用服务端将与该用户对应的`accid`和`token`等信息返回给应用客户端。此时，应用客户端需要负责保存`accid`和`token`的映射关系。
5. 当应用客户端需要调用云信的 IM 服务时，需要先进行`token`验证，以登录 IM 服务。
6. `token`验证成功后，应用客户端登录 IM 服务成功。之后用户便可调用 NIM SDK 的相关接口使用 IM 服务，如进行 IM 消息收发。

::: note note
- 终端用户使用云信 IM 服务时，应用本身的用户帐号和云信的 IM 账号（`accid`）**彼此独立**。云信的 IM 账号只用于云信 IM 服务的鉴权，**IM 账号并不等同于应用的用户账号**。
- 应用的用户帐号和密码，与云信登录 IM 使用的 `accid`和`token` 完全不一致。`accid`和`token` 不由终端用户创建，而是由应用服务端分配，以保证安全性。
:::




## 前提条件

实现登录 IM 前，请确保已：
- 完成[初始化](https://doc.yunxin.163.com/messaging/docs/zE1MTQwMTY?platform=pc)。
- 已在云信控制台配置应用的 [IM 登录策略](https://doc.yunxin.163.com/messaging/docs/DYyMDc4Njg?platform=pc#控制台配置)。如未配置相应的登录策略，可能导致后续调用登录接口时因无登录权限而报错（状态码：403）。
- （可选）已在控制台[配置客户端应用标识](https://doc.yunxin.163.com/console/docs/jU3MDY4Njk?platform=console#标识管理)。



## 实现登录 IM


### 步骤1：准备 Token


登录 IM 需要通过`token`进行鉴权。云信提供静态和动态这两种 `token` 类型，您可根据业务需求进行选择。

- 静态`token`：默认为永久有效。如有需要，可通过云信服务端 API [主动刷新 Token](https://doc.yunxin.163.com/messaging/docs/DUxNDQ3NjA?platform=server)。


- 动态`token`：具备时效性，可在生成时设置`token`的有效期。


#### **获取静态Token**

- 方式1：在控制台获取静态 Token

    如果您只需要进行简单的**体验或者快速测试**，那么可以在云信控制台创建测试用的 IM 账号，并获取与该 IM 账号相应的**静态`token`**。具体参见[注册调试用的 IM 账号](https://doc.yunxin.163.com/messaging/docs/DI0MTcyNzI?platform=pc#注册-im-账号)。获取的静态token可用于下文提及的[静态 Token 登录](#静态Token登录)的鉴权。


- 方式2：调用服务端 API 获取静态 Token

    如果您有正式的**生产环境**，且您的业务**仅需保障基础的用户信息安全**，那么需要通过云信 IM 服务端 API 注册 IM 账号，并获取与之相对应的**静态`token`**。具体参见[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server)。获取的静态`token`可用于[静态 Token 登录](#静态Token登录)的鉴权



#### **获取动态Token**

如果您有正式的**生产环境**，且您的业务**对用户信息安全有较高的要求**，可使用动态`token`。动态token可用于[动态 Token 登录](#动态Token登录)的鉴权。

1. [注册云信 IM 账号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server)，获取 IM 账号（`accid`）和静态`token`。

2. 基于App Key、App Secret 和`accid`，通过[约定算法](https://doc.yunxin.163.com/TM5MzM5Njk/docs/zE2NzA3Mjc?platform=server#动态token鉴权)在应用服务端生成**动态`token`**。

3. 客户端可通过在初始化时实现 `RegReloginRequestToeknCb` 方法，从回调中获取动态 `token`。



#### **动态获取第三方鉴权扩展信息**

NIM SDK 也支持获取动态的登录自定义扩展字段 `LoginParams::login_ex_`。动态 `login_ex_` 适用于所有登录模式，其中，在第三方回调登录模式中使用动态 `login_ex_`时，第三方服务器可以使用该字段来进行鉴权。

客户端可通过在初始化时实现 `RegRequestLoginExtensionCb` 方法，从回调中获取动态 `login_ex_`。




### 步骤2：注册相关监听


调用登录接口前，需要先实现监听 IM 登录断开事件和自动重连事件。

#### 监听登录断开事件

注册[`RegDisconnectCb`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#ad30bb87684fddd8fe59b06782077589f) 回调，监听是否掉线，断开连接。该回调主要用于客户端 UI 刷新。


示例代码如下：

```
Client::RegDisconnectCb(
    []() {
        // process disconnect event
        // ......
    },
    "");
```


#### 监听自动重连事件

SDK 提供了断网自动重连机制（自动重新建立与网易云信服务器的连接并重新登录），您可以注册[`RegReloginCb`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a8b81e6a7b9de85714e86deca471e41ae)回调，监听自动重连事件。一些特殊的登录错误需要通过该回调返回，包括 App Key 未设置、参数错误、密码错误、多端登录冲突、[账号被封禁](https://doc.yunxin.163.com/messaging/docs/TUzOTA4NTY?platform=server)、操作过于频繁等，具体请参考[`NIMResCode`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/public__defines_8h.html#a5083ca8fcdb1153b725f6a55e6cbd647)，建议在集成时能尽可能在上层应用考虑应对逻辑。

例如，自动重连时如果用户名和密码不匹配，上层应用需实现**登出并提示用户手动登录**或是**从应用服务器刷新相应的用户名和密码**等逻辑。


::: note note 
- 网络状态较差时容易导致自动重连发生网络超时错误，此时上层应用无需处理，SDK 会持续有策略地重连。
- 手动登录阶段有重连次数上限，初始化可配置，默认最多重试三次，三次都失败会触发登录断开事件，此时需要上层重新调用登录接口。登录保持阶段重连无上限，在第一次断开连接时会触发登录断开事件。
:::


### 步骤3：登录 IM


NIM SDK 登录方式分为静态`token`登录、动态`token`登录和通过第三方回调登录，分为对应[静态 Token 鉴权](https://doc.yunxin.163.com/messaging/docs/zE2NzA3Mjc?platform=server#静态token鉴权)、[动态 Token 鉴权](https://doc.yunxin.163.com/messaging/docs/zE2NzA3Mjc?platform=server#动态token鉴权)和[通过第三方回调鉴权](https://doc.yunxin.163.com/messaging/docs/zE2NzA3Mjc?platform=server#基于第三方回调的鉴权)三种鉴权方式。

您可按需实现**一种或多种**登录方式。 

SDK 通过 `auth_type_`（NIMAuthType） 来定义鉴权方式：

枚举值|对应值|说明
----|----|---
`kNIMAuthTypeDefault`|0|默认登录方式，静态 token 鉴权
`kNIMAuthTypeBySecretToken`|1|使用 App secret 生成的 token 登录，动态 token 鉴权
`kNIMAuthTypeByAppToken`|2|使用第三方回调服务器生成的凭证，第三方回调鉴权


#### <span id="静态Token登录">**静态 Token 登录**</span>




调用[`Login`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a0e8d4b3f4cfcad3cd4bdffd98bdba4c4)方法进行手动登录。

<table>
    <thead><tr> <th style="width:150px">参数</th><th style="width:120px">类型</th><th>必填</th><th>说明</th></tr></thead> 
    <tr> <td>app_key</td><td>std::string</td><td>否</td><td>您的应用在云信的账号（App Key）<br>如果不填，则使用初始化时填入 App Key；如果调用本接口时填入，则使用新填入的 App Key</td></tr>
    <tr> <td>account</td><td>std::string</td><td>是</td><td>用户的 IM 账号（即accid）</td></tr>
    <tr> <td>password</td><td>std::string</td><td>是</td><td>获取到的静态token</td></tr>
    <tr> <td>json_extension</td><td>std::string</td><td>否</td><td> JSON 扩展参数，主要用于指定登录信息 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_login_params.html" target="_blank">LoginParams</a>，包括自定义登录数据（custom_data_）、鉴权方式 （auth_type_）以及第三方回调扩展信息（login_ex_）。<ul><li>静态 token 模式下，auth_type_ 为 kNIMAuthTypeDefault</li><li>可通过 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#ad44d250ee8833e2febe798e234e2a6d5" target="_blank">LoginCustomDataToJson</a> 接口将 LoginParams 转换为 JSON 格式字符串</li></ul> </td></tr>
    <tr> <td>cb</td><td>LoginCallback</td><td>否</td><td>登录流程的回调函数</td></tr>
</table>


示例代码如下：

```
//静态token的模式登录IM
LoginParams login_param;
login_param.auth_type_ = kNIMAuthTypeDefault;
std::string login_param_str;
Client::LoginCustomDataToJson(login_param, login_param_str);
Client::Login("appkey", "accid", "password", [](const LoginRes& res) {
    if (res.res_code_ != kNIMResSuccess){
        // login failed
    } else if (res.login_step_ == kNIMLoginStepLogin){
        // login success
    }
}, login_param_str);
```



#### <span id="动态Token登录">**动态 Token 登录**</span>

NIM SDK 支持动态 `token` 登录这一登录方式。该登录方式的 `token` 具备时效性，可有效提升 `token` 破解难度，降低密码泄露风险。

要实现动态登录 IM，需完成如下两步操作：

1. 初始化时，实现 `RegReloginRequestToeknCb` 方法获取上文提及的[基于App Secret生成的动态Token](#获取动态token)。
   **示例代码如下**：
    ```
    Client::RegReloginRequestToeknCb([](std::string* token) {
        std::string login_token;
        // get token from your application server
        // ......
        *token = login_token;
    });
    ``` 

2. 调用[`Login`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a0e8d4b3f4cfcad3cd4bdffd98bdba4c4)方法进行手动登录。

    <table>
        <thead><tr> <th style="width:150px">参数</th><th style="width:120px">类型</th><th>必填</th><th>说明</th></tr></thead> 
        <tr> <td>app_key</td><td>std::string</td><td>否</td><td>您的应用在云信的账号（App Key）<br>如果不填，则使用初始化时填入 App Key；如果调用本接口时填入，则使用新填入的 App Key</td></tr>
        <tr> <td>account</td><td>std::string</td><td>是</td><td>用户的 IM 账号（即accid）</td></tr>
        <tr> <td>password</td><td>std::string</td><td>是</td><td>静态 token。当 IM 采用动态 token 鉴权方式登录时，无需提供静态 token<br>如果您的应用启用了云信的聊天室功能，并且采用<strong>非独立模式</strong>登录时（调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim__chatroom_1_1_chat_room.html#a2927f3d270f3ac3fa2a62095ba8eb41a" target="_blank">ChatRoom::Enter</a> 接口登录聊天室时需要 IM 的静态 token），那么此处需要传入静态 token</td></tr>
        <tr> <td>json_extension</td><td>std::string</td><td>是</td><td> JSON 扩展参数，主要用于指定登录信息 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_login_params.html" target="_blank">LoginParams</a>，包括自定义登录数据（custom_data_）、鉴权方式 （auth_type_）以及第三方回调扩展信息（login_ex_）。<ul><li>动态 token 模式下，auth_type_ 必须设置为 kNIMAuthTypeBySecretToken</li><li>可通过 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#ad44d250ee8833e2febe798e234e2a6d5" target="_blank">LoginCustomDataToJson</a> 接口将 LoginParams 转换为 JSON 格式字符串</li></ul> </td></tr>
        <tr> <td>cb</td><td>LoginCallback</td><td>否</td><td>登录流程的回调函数</td></tr>
    </table>

    **示例代码如下**：

    ```
    LoginParams login_param;
    login_param.auth_type_ = kNIMAuthTypeBySecretToken;
    std::string login_param_str;
    Client::LoginCustomDataToJson(login_param, login_param_str);
    Client::Login("appkey", "accid", "", [](const LoginRes& res) {
        if (res.res_code_ != kNIMResSuccess){
            // login failed
        } else if (res.login_step_ == kNIMLoginStepLogin){
            // login success
        }
    }, login_param_str);
    ```



#### <span id="通过第三方回调登录">**通过第三方回调登录**</span>




如采用该登录方式，**云信服务端不做 IM 登录鉴权**，鉴权工作需由指定的第三方服务器（可以是应用服务器）进行。

实现该登录方式，需完成如下 4 步操作：

1. 前往云信控制台，并进入**IM 即时通讯 > 功能配置 > 第三方回调**配置第三方回调的环境地址（即第三方服务器地址）和回调失败时放行（通过）与否。


    ![第三方回调配置文案优化后.png](https://yx-web-nosdn.netease.im/common/3399fe2b490e47fb56cd6575faefa6d5/第三方回调配置文案优化后.png)

2. 若您的应用需要采用第三方服务器的动态 Token 或者动态第三方回调扩展信息鉴权，那么需要在初始化时实现 `RegReloginRequestToeknCb` 和 `RegRequestLoginExtensionCb` 方法，SDK 会在登录过程时动态获取第三方回调的动态 Token 和动态扩展字段（`login_ex_`）。

   **示例代码如下**：
   ```
    Client::RegReloginRequestToeknCb([](std::string* token) {
        std::string login_token;
        // get token from your application server
        // ......
        *token = login_token;
    });
    Client::RegRequestLoginExtensionCb([this](std::string* extension) {
        std::string login_extension;
        // get login extension from your application server
        // ......
        *extension = login_extension;
    });
   ``` 

3. 调用[`Login`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a0e8d4b3f4cfcad3cd4bdffd98bdba4c4)方法进行动态登录。

    <table>
        <thead><tr> <th style="width:150px">参数</th><th style="width:120px">类型</th><th>必填</th><th>说明</th></tr></thead> 
        <tr> <td>app_key</td><td>std::string</td><td>否</td><td>您的应用在云信的账号（App Key）<br>如果不填，则使用初始化时填入 App Key；如果调用本接口时填入，则使用新填入的 App Key</td></tr>
        <tr> <td>account</td><td>std::string</td><td>是</td><td>用户的 IM 账号（即accid）</td></tr>
        <tr> <td>password</td><td>std::string</td><td>是</td><td>静态 token。当 IM 采用第三方回调鉴权方式登录时，无需提供静态 token<br>如果您的应用启用了云信的聊天室功能，并且采用<strong>非独立模式</strong>登录时（调用 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim__chatroom_1_1_chat_room.html#a2927f3d270f3ac3fa2a62095ba8eb41a" target="_blank">ChatRoom::Enter</a> 接口登录聊天室时需要 IM 的静态 token），那么此处需要传入静态 token</td></tr>
        <tr> <td>json_extension</td><td>std::string</td><td>是</td><td> JSON 扩展参数，主要用于指定登录信息 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/structnim_1_1_login_params.html" target="_blank">LoginParams</a>，包括自定义登录数据（custom_data_）、鉴权方式 （auth_type_）以及第三方回调扩展信息（login_ex_）。<ul><li>第三方回调模式下，auth_type_ 必须设置为 kNIMAuthTypeByAppToken</li><li>可通过 <a href="https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#ad44d250ee8833e2febe798e234e2a6d5" target="_blank">LoginCustomDataToJson</a> 接口将 LoginParams 转换为 JSON 格式字符串</li></ul> </td></tr>
        <tr> <td>cb</td><td>LoginCallback</td><td>否</td><td>登录流程的回调函数</td></tr>
    </table>


    **示例代码如下**：

    ```
    //第三方鉴权的模式登录IM
    LoginParams login_param;
    login_param.auth_type_ = kNIMAuthTypeByAppToken;
    std::string login_param_str;
    Client::LoginCustomDataToJson(login_param, login_param_str);
    Client::Login("appkey", "accid", "", [](const LoginRes& res) {
        if (res.res_code_ != kNIMResSuccess){
            // login failed
        } else if (res.login_step_ == kNIMLoginStepLogin){
            // login success
        }
    }, login_param_str);
    ```


4. 发起[登录相关回调](https://doc.yunxin.163.com/messaging/docs/jc3MzA5NTk?platform=server)的请求，由第三方服务器进行鉴权并判定 IM 登录事件是否放行通过。

    若不通过，云信服务端将返回第三方回调错误码


### 步骤4（可选）：主动查询登录状态

调用[`GetLoginState`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a953eba9ba17ecfdb53145d658b36ffbf)方法主动查询当前 IM 账号的登录状态。

返回的登录状态（[`NIMLoginState`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/nim__client__def_8h.html#aba1faba62eb6c981f052fee136d5519a)）包括：

- `kNIMLoginStateLogin`：已登录
- `kNIMLoginStateUnLogin `：未登录

## 相关信息

### 登录过程

登录过程中的状态可查看 `NIMLoginStep` 枚举：

| 枚举值               | 说明                 |
|----------------------|----------------------|
| `kNIMLoginStepLinking `  | 正在连接服务器  |
| `kNIMLoginStepLink`   | 连接服务器成功 |
| `kNIMLoginStepLogining `  | 正在登录 |
| `kNIMLoginStepLogin `  | 登录成功 |


### <span id="断网重连">断网重连</span>

SDK 提供了自动重连机制（自动重新建立与网易云信服务器的连接并重新登录），您可以注册[`RegReloginCb`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a8b81e6a7b9de85714e86deca471e41ae)回调，监听自动重连事件。

SDK 登录成功后，网络不佳导致 SDK 与云信服务端连接断开时会自动进行重连，**不需要上层开发者去做额外的重登逻辑**。


::: note notice
重试次数超过预定上限（**默认重连 3 次**）时，SDK 不会继续重连。可以在初始化参数中（`SDKConfig`）自行设置重试次数（`login_max_retry_times`）。
:::


### 多端登录与互踢

当前 NIM SDK 支持配置四种不同的 IM 多端登录与互踢策略，具体参见[多端登录与互踢]()。



### 相关辅助方法


`Client` 类中提供了辅助方法：


方法| 说明
---- | -------------- 
[`GetCurrentUserAccount`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a0fdf679490cca10dcef71e4e74903ec4)  | 获取当前登录的 IM 账号。如果没有登录成功，会返回空字符串""
[`GetServerCurrentTime`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a391a12a15919b89b21e0202452bcb8f0) | 查询云信服务端当前的时间。
