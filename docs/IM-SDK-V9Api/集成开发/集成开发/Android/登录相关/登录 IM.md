
<!-- keywords: 即时通讯,IM,登录, 登录流程, 账号集成,账号集成与登录, 登录状态 -->



完成 NIM SDK 的初始化之后，用户需要先调用 SDK 的登录接口登录 IM。登录成功后，用户才能正常调用消息和会话等其他 SDK 接口。


本文介绍账号集成与登录的技术原理、实现 IM 登录的流程、IM 登录状态转换流程，以及[相关常见问题](#常见问题)。



## 技术原理



<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/f7d332058c2fed770bc0691fb3a2dd18/账号集成与登录原理新图.png" />



IM 的登录与账号集成密切相关。上图展示了应用集成 NIM SDK 后，从账号集成到登录 IM 成功的主要流程：

1. 用户在应用客户端注册用户账号时，由应用服务端向云信服务端发起[创建 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)的请求。
2. IM 账号创建成功后，云信服务端会返回该 IM 账号（即 `accid`）和 `token` 等信息。此时，应用服务端需要负责保存 `accid` 和 `token` 的映射关系。
3. 应用客户端发起登录请求时，先走应用自有的登录验证逻辑，如账号和密码的验证。
4. 验证成功后，应用服务端将与该用户对应的 `accid` 和 `token` 等信息返回给应用客户端。此时，应用客户端需要负责保存 `accid` 和 `token` 的映射关系。
5. 当应用客户端需要调用云信的 IM 服务时，需要先进行 `token` 验证，以登录 IM 服务。
6. `token` 验证成功后，应用客户端登录 IM 服务成功。之后用户便可调用 NIM SDK 的相关接口使用 IM 服务，如进行 IM 消息收发。

::: note note
- 终端用户使用云信 IM 服务时，应用本身的用户账号和云信的 IM 账号（`accid`）**彼此独立**。云信的 IM 账号只用于云信 IM 服务的鉴权，**IM 账号并不等同于应用的用户账号**。
- 应用的用户账号和密码，与云信登录 IM 使用的 `accid` 和 `token` 完全不一致。`accid` 和 `token` 不由终端用户创建，而是由应用服务端分配，以保证安全性。
:::


## 前提条件

- 已完成[初始化](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android)。
- 已在云信控制台配置应用的 [IM 登录策略](https://doc.yunxin.163.com/messaging/guide/jE0NjA3NTU?platform=android#控制台配置)。如未配置相应的登录策略，可能导致后续调用登录接口时因无登录权限而报错（状态码：403）。
- （可选）已在控制台[配置客户端应用标识](https://doc.yunxin.163.com/console/docs/jU3MDY4Njk?platform=console#配置客户端应用标识)。

## 实现登录 IM


### 步骤1：准备 Token


登录 IM 需要通过 Token 进行鉴权。云信支持静态和动态两种 Token 类型，您可根据业务需求进行选择。

- 静态 Token：默认为永久有效。如有需要，可通过云信服务端 API [主动刷新 Token](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)。


- 动态 Token：具备时效性，可在生成时设置有效期。

#### **获取静态Token**


- 方式一：在控制台获取静态 Token

    如果您只需要进行简单的**体验或者快速测试**，那么可以在云信控制台创建测试用的 IM 账号，并获取与该 IM 账号相应的静态`token`，具体参见[注册调试用的 IM 账号](https://doc.yunxin.163.com/messaging/guide/jMwMTQxODk?platform=android#注册-im-账号)。获取的静态`token`可用于下文提及的[静态 Token 登录](#静态Token登录)。

- 方式二：调用服务端 API 获取静态 Token

    如果您有正式的**生产环境**，且您的业务**仅需保障基础的用户信息安全**，那么可通过云信 IM 服务端 API 注册 IM 账号，并获取与之相对应的静态`token`，具体参见[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)。获取的静态`token`可用于[静态 Token 登录](#静态Token登录)的鉴权。



#### **获取动态Token**

如果您有正式的**生产环境**，且您的业务**对用户信息安全有较高的要求**，可使用动态 `token`。动态 `token` 可用于[动态 Token 登录](#动态Token登录)的鉴权。

1. [注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)，获取 IM 账号（`accid`）。

2. 基于 App Key、App Secret 和 `accid`，通过[约定算法](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)在应用服务端生成动态 Token。

3. 客户端可通过在初始化时实现 `SDKOptions#AuthProvider` 方法，从回调中获取动态 `token`。

    ```
    SDKOptions options = new SDKOptions();
    options.authProvider = new AuthProvider() {
        @Override
        public String getToken(String account) {
            return "your_token";
        }
    };
    ```

#### **获取动态LoginExt**

NIM SDK 也支持获取动态的登录自定义扩展字段 `loginExt`。动态 `loginExt` 适用于所有登录模式，其中，在第三方回调登录模式中使用动态 `loginExt`时，第三方服务器可以使用该字段来进行鉴权。

客户端可通过在初始化时实现 `SDKOptions#loginExtProvider` 方法，从回调中获取动态 `loginExt`。

```
options.loginExtProvider = new LoginExtProvider() {

    @Override
    public String getLoginExt(String account) {
        return "your_login_ext";
    }
};
```


### 步骤2：监听登录相关回调


#### 监听登录状态


调用[`observeOnlineStatus`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service_observer.html#adf734324bdc99f79b88aaba8899e76ab)方法注册在线状态变化观察者，监听登录状态变化。注册后，观察者（`Observer`）的`onEvent`回调函数会立即被调用一次，告知观察者当前的登录状态（[`StatusCode`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/enumcom_1_1netease_1_1nimlib_1_1sdk_1_1_status_code.html)）。


- `StatusCode`枚举各属性的**详细说明和具体转换流程**，参见文末的[登录状态转换流程](#登录状态转换流程)。

- `StatusCode`枚举的每个属性包含一个 int 类型的 value 和一个 String 类型的 desc。通过云信 IM 服务端接口[封禁 IM 账号](https://doc.yunxin.163.com/messaging/guide/TUzOTA4NTY?platform=server#封禁账号)时，如果配置了`kickNotifyExt`，则会表现在`onEvent`回调函数的 desc 变量中。


示例代码如下：

```java
NIMClient.getService(AuthServiceObserver.class).observeOnlineStatus(
	new Observer<StatusCode> () {
		public void onEvent(StatusCode status) {
        //获取状态的描述
        String desc = status.getDesc();
			if (status.wontAutoLogin()) {
                // 被踢出、账号被禁用、密码错误等情况，自动登录失败，需要返回到登录界面进行重新登录操作
            }
		}
}, true);
```
#### 监听数据同步状态


调用[`observeLoginSyncDataStatus`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service_observer.html#a6944be8f502e360e58e4ef00515988ac)方法注册观察者，监听登录后的数据同步状态（`LoginSyncStatus`）。 

登录 IM 成功后，SDK 会自动同步群信息，离线消息，漫游消息，系统通知等数据。**数据同步完成时，整个登录过程才算真正完成**。


| <div style="width:160px">LoginSyncStatus属性</div> | 说明 |
| :-------: | :--------|
| `NO_BEGIN` | 未开始同步 |
| `BEGIN_SYNC` | 开始同步（正在同步）<ul><li>同步开始时，SDK 数据库中的数据可能还是旧数据</li><ul><li>如果是首次登录，那么 SDK 数据库中还没有数据</li><li>重新登录时 SDK 数据库中还是上一次退出时保存的数据</li></ul></li><li>在同步过程中，SDK 数据的更新会通过相应的监听接口发出数据变更通知</li></ul> |
| `SYNC_COMPLETED` | 同步完成。SDK 数据库已完成更新|

示例代码如下：

```java
NIMClient.getService(AuthServiceObserver.class).observeLoginSyncDataStatus(new Observer<LoginSyncStatus>() {
    @Override
    public void onEvent(LoginSyncStatus status) {
        if (status == LoginSyncStatus.BEGIN_SYNC) {
            LogUtil.i(TAG, "login sync data begin");
        } else if (status == LoginSyncStatus.SYNC_COMPLETED) {
            LogUtil.i(TAG, "login sync data completed");
        }
    }
}, register);
```

#### 监听数据准备完成回调

发送消息等后续操作要求数据库处于开启状态，否则可能导致发送消息失败，或者阻塞等待数据库开启。

当手动登录或自动登录成功后，云信 IM 开始打开数据库，调用 `observeDataReady` 方法注册观察者，监听数据库成功开启的回调。 


:::note note 
首次登录成功后开启数据库会回调，不登出再调用登录不会多次回调。
:::


### 步骤3：登录 IM 


#### <span id="登录方式概览">登录方式概览</span>




NIM SDK 登录方式分为两大类，即手动登录和自动登录。其中手动登录可进一步分为静态`token`登录、动态`token`登录和通过第三方回调登录。 

您可按需实现**一种或多种**手动登录方式，并**在手动登录成功后**，实现自动登录。 

<div style="width:100px">登录方式</div> | 子方式 | 鉴权方式 | 使用场景
---- | -------------- | ---------
手动登录 |  [静态 Token 登录](#静态Token登录)  | [静态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#静态token鉴权)  | 如下登录场景，用户需要手动登录 IM：<ul><li>在新设备上首次登录 IM</li><li>被同时在线的[其他设备踢下线](https://doc.yunxin.163.com/messaging/guide/jY2MDg0OTQ?platform=android)后再次登录 IM</li><li>切换 IM 账号后再次登录 IM</li><li>[注销登录](https://doc.yunxin.163.com/messaging/guide/TAyOTEyMTk?platform=android)后再次登录 IM</li></ul>
^^ | [动态 Token 登录](#动态Token登录)    | [动态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权) |  ^^
^^   |   [通过第三方回调登录](#通过第三方回调登录)   |  [通过第三方回调鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#基于第三方回调的鉴权)  | ^^
[自动登录](#自动登录)   |  继承手动登录的方式  |   继承手动登录的鉴权方式    |  应用被清理后，用户再次点击应用图标启动应用时，无需输入用户名和密码即可完成登录的场景。**自动登录需在手动登录成功后使用**     

::: note note 
**推荐**在手动登录成功后，将`accid`和`token`**保存到本地**，方便下次应用启动进行初始化时在`SDKOptions`的`LoginInfo`中传入，实现自动登录。更多相关说明，参见[IM 登录最佳实践](https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android)。您也可以参考该文档中提供的 **Sample Code** 实现 IM 登录。
:::

#### <span id="手动登录">方式1：手动登录</span>


##### <span id="静态Token登录"><b>静态 Token 登录</b></span>

调用[`AuthService#login`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#ae9f6be76fc29def4b382bfc813ef0214)方法手动登录 IM。调用时需将`authType`参数设置为 0。

调用后，NIM SDK 会自动连接云信服务端，传递用户信息，返回登录结果。登录过程中可主动取消登录。如果因为网络或其他原因导致云信服务端长时间未响应，用户也没有主动取消登录，NIM SDK 将在 45 秒后自动重新连接云信服务端，并返回错误码，错误码详情参见下文的[手动登录错误码](#手动登录错误码)。

<div style="width:130px">[`LoginInfo`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html) 参数</div> |是否必传|  说明  
-------- | --- |------
`account` | 是| 用户的 IM 账号，即 `accid` 
`token` | 是 | 获取到的静态 `token`
`authType` | 否 | 登录 IM 的鉴权方式。采用静态`token`登录时，使用**默认的 0** 即可，即静态 `token` 鉴权
`appKey` | 否 | 当前应用的 App Key，一个 App Key 对应一个账号体系<note type=note>如果不填，则优先使用初始化时`SDKOptions`中配置的 App Key；如果`SDKOptions`中未配置，则使用 `AndroidManifest` 中配置的 App Key。</note> 
`customClientType` | 否| 自定义客户端类型，小于或等于 0 则视为没有自定义类型 
`loginExt`|否|登录自定义扩展字段，长度上限为 1k 字符。若在初始化时实现了 `loginExtProvider` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先取返回值，忽略此处输入的 loginExt 值。

示例代码如下：

```java
//静态token的模式登录IM
public class LoginActivity extends Activity {
    public void doLogin() {
        LoginInfo info = new LoginInfo(); 
        RequestCallback<LoginInfo> callback =
            new RequestCallback<LoginInfo>() {
                    @Override
                    public void onSuccess(LoginInfo param) {
                        LogUtil.i(TAG, "login success");
                        // your code
                    }

                    @Override
                    public void onFailed(int code) {
                        if (code == 302) {
                            LogUtil.i(TAG, "账号密码错误");
                            // your code
                        } else {
                            // your code
                        }
                    }

                    @Override
                    public void onException(Throwable exception) {
                        // your code
                    }
        };

        //执行手动登录
        NIMClient.getService(AuthService.class).login(info).setCallback(callback);
    }
}
```




##### <span id="动态Token登录"><b>动态 Token 登录</b></span>

NIM SDK 支持动态 `token` 登录这一登录方式。该登录方式的 `token` 具备时效性，可有效提升 `token` 破解难度，降低密码泄露风险。

要实现动态`token`登录 IM，需完成如下两步操作：


1. [初始化](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android#步骤2初始化-sdk)时，实现[`SDKOptions#AuthProvider`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_provider.html) 方法获取上文中提及的[基于App Secret生成的动态Token](#获取动态token)。

    ```
    SDKOptions options = new SDKOptions();
    options.authProvider = new AuthProvider() {
        @Override
        public String getToken(String account) {
            return "your_token";
        }
    };    
    ```

2. 调用`AuthService#login`方法手动登录 IM，调用时需将 `authType`设置为 1。

    调用后，NIM SDK 会自动连接云信服务端，传递用户信息，返回登录结果。登录过程中可主动取消登录。如果因为网络或其他原因导致云信服务端长时间未响应，用户也没有主动取消登录，NIM SDK 将在 45 秒后自动重新连接云信服务端，并返回错误码，错误码详情参见下文的[手动登录错误码](#手动登录错误码)。



    具体参数说明如下：

    <div style="width:130px">[`LoginInfo`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html) 参数</div> |是否必传|  说明  
    -------- | --- |------
    `account` | 是| 用户的 IM 账号，即`accid` 
    `authType` | 该登录方式必传 | **采用动态`token`登录时必须传入 1**，表示通过动态`token`鉴权，动态`token`[基于 App Secret 计算生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)
    `token` | 否 | 静态 `token`。当 IM 采用动态 `token` 鉴权方式且在初始化时实现了 `SDKOptions#AuthProvider` 方法，回调该方法时返回了非空的 token 值，那么优先使用返回的动态 token 进行鉴权；如果回调返回空值，会返回错误码，此时若已传入静态 token，则取此处的静态 token 进行鉴权；如果回调返回空值且未传入静态 token，则直接返回 414 错误码<note type=notice>如果您的应用启用了云信的聊天室功能，并且采用**非独立模式&静态 token 登录方式**鉴权时，那么此处必须传入静态 token。传入后，后续**非独立模式的聊天室静态登录**时会使用该静态 token</note>
    `appKey` | 否 | 当前应用的 App Key，一个 App Key 对应一个账号体系<note type=note>如果不填，则优先使用初始化时`SDKOptions`中配置的 App Key；如果`SDKOptions`中未配置，则使用 `AndroidManifest` 中配置的 App Key。</note> 
    `customClientType` | 否| 自定义客户端类型，小于或等于 0 则视为没有自定义类型 
    `loginExt` | 否 | 登录自定义扩展字段，长度上限为 1k 字符。若在初始化时实现了 `loginExtProvider` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先取回调返回值，忽略此处输入的 loginExt 值。

    :::note notice
    - 使用动态 token 登录（即登录方式 authType 为 1）时，如果注册了动态 token 回调，但返回空值且未传入静态 token（可能第三方服务器设置了动态时间），则直接返回 414 错误码，云信内部不做登录请求。
    - 若注册了回调，回调返回空值，但是登录信息中已传入静态 token，也会返回相关错误码，但是此时，不中断重连，即继续走重连机制（若在初始化设置了自动重连的次数限制，注意该场景下的自动重连次数不计入），等待动态 Token 的传入。
    :::


##### <span id="通过第三方回调登录"><b>通过第三方回调登录</b></span>

如采用该登录方式，**云信服务端不做 IM 登录鉴权**，鉴权工作需由指定的第三方服务器（可以是应用服务器）进行。

1. 实现该登录方式，需[开通和配置第三方服务](https://doc.yunxin.163.com/messaging/guide/jI3ODc2ODE?platform=server#开通和配置第三方服务)。

2. 若您的应用需要采用第三方服务器的动态 Token 或者动态 LoginExt 鉴权，那么需要在初始化时实现 `SDKOptions#authProvider` 和 `SDKOptions#loginExtProvider` 方法，SDK 会在登录过程时动态通过 Delegate 方法获取第三方回调的动态 Token 和动态扩展字段（`loginExt`）。

    示例代码如下：
    ```
    SDKOptions options = new SDKOptions();
    options.authProvider = new AuthProvider() {
        @Override
        public String getToken(String account) {
            return "your_token";
        }
    };

    options.loginExtProvider = new LoginExtProvider() {

        @Override
        public String getLoginExt(String account) {
            return "your_login_ext";
        }
    };
    ```

3. 调用[`AuthService#login`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#ae9f6be76fc29def4b382bfc813ef0214)方法手动登录 IM，调用时`authType`必须传入 2。调用后，NIM SDK 会自动连接云信服务端，传递用户信息，返回登录结果。登录过程中可主动取消登录。如果因为网络或其他原因导致云信服务端长时间未响应，用户也没有主动取消登录，NIM SDK 将在 45 秒后自动重新连接云信服务端，并返回错误码，错误码详情参见下文的[手动登录错误码](#手动登录错误码)。
   

    具体参数说明如下：



    <div style="width:130px">[`LoginInfo`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html) 参数</div> |是否必传|  说明  
    -------- | --- |------
    `account` | 是| 用户的 IM 账号，即`accid` 
    `authType` | 该登录方式必传 | 登录 IM 的鉴权方式，采用该登录方式时必须传入 2，表示通过第三方回调进行鉴权
    `token` | 否 | 静态 `token`。当 IM 采用第三方回调鉴权方式且在初始化时实现了 `SDKOptions#AuthProvider` 方法，回调该方法时返回了非空的 token 值，那么优先使用返回的第三方动态 token 进行鉴权；如果回调返回空值，会返回错误码，如果此时已传入静态 token，则取此处的静态 token 进行鉴权<note type=notice>如果您的应用启用了云信的聊天室功能，并且采用**非独立模式&静态 token 登录方式**鉴权时，那么此处必须传入静态 token。传入后，后续**非独立模式的聊天室静态登录**时会使用该静态 token</note>
    `appKey` | 否 | 当前应用的 App Key，一个 App Key 对应一个账号体系<note type=note>如果不填，则优先使用初始化时`SDKOptions`中配置的 App Key；如果`SDKOptions`中未配置，则使用 `AndroidManifest` 中配置的 App Key。</note> 
    `customClientType` | 否| 自定义客户端类型，小于或等于 0 则视为没有自定义类型 
    `loginExt` |否 | 登录自定义扩展字段，长度上限为 1k 字符。第三方服务器可以使用该字段来鉴权。若在初始化时实现了 `SDKOptions#loginExtProvider` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先使用返回的第三方动态 loginExt 值进行鉴权，如果回调返回空值，会返回错误码，如果此时已传入静态 loginExt，则取此处手动传入的 loginExt 进行鉴权。

    :::note notice
    - 使用第三方回调登录（即登录方式 authType 为 2）时，如果注册了第三方动态 token 和 loginExt 回调，但都返回空值且未传入静态 token 和 loginExt（可能第三方服务器设置了动态时间），则直接返回 414 错误码，云信内部不做登录请求。
    - 若注册了回调，回调返回空值，但是登录信息中已传入静态鉴权字段，也会返回相关错误码，但是此时，不中断重连，即继续走重连机制（若在初始化设置了自动重连的次数限制，注意该场景下的自动重连次数不计入），等待第三方动态 Token 或 loginExt 的传入。
    :::



    


4. 发起[登录相关回调](https://doc.yunxin.163.com/messaging/guide/jc3MzA5NTk?platform=server)的请求，由第三方服务器进行鉴权并判定 IM 登录事件是否放行通过。

    若不通过，云信服务端将返回 302 错误码。


#### <span id="自动登录">方式2：自动登录</span>



自动登录一般用于应用被清理后，用户再次点击应用图标启动应用时，无需输入用户名和密码即可完成登录的场景。此时应用可以在无网络、未登录成功的状态下直接访问用户本地 SDK 数据。自动登录与手动登录在客户端侧和服务端逻辑上的区别，参见文末的[常见问题](#手动登录和自动登录的主要区别是什么)。



实现自动登录的方式为，在调用[初始化的几个方法](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android#步骤2初始化-sdk)时，传入[`LoginInfo`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html)。

::: note note 
**推荐**参考[自动登录最佳实践](https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android#自动登录)和[登录状态处理最佳实践](https://doc.yunxin.163.com/messaging/guide/DE1NjMxNjU?platform=android#登录状态处理)实现自动登录以及相应的登录状态处理逻辑。
:::

<br>

示例代码如下（仅以调用`NIMClient#init`方法为例）：

```java
public class NimApplication extends Application {

	public void onCreate() {
		// ... your codes

		NIMClient.init(this, loginInfo(), options());

		// ... your codes
	}

	private LoginInfo loginInfo() {
	    // 从本地读取上次登录成功时保存的用户登录信息
        String account = Preferences.getUserAccount();
        String token = Preferences.getUserToken();

        if (!TextUtils.isEmpty(account) && !TextUtils.isEmpty(token)) {
            DemoCache.setAccount(account.toLowerCase());
            return new LoginInfo(account, token);
        } else {
            return null;
        }
    }
}
```





### 步骤4（可选）：主动查询登录状态


SDK支持通过[`NIMClient#getStatus`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a88efc6b9ae135e431ebe968bf2158d5a) 方法主动查询当前账号是否处于在线状态。

返回当前用户的登录的状态枚举值说明，请参见下文的[登录状态转换流程](#登录状态转换流程)。


示例代码:
```
if (NIMClient.getStatus() == StatusCode.LOGINED) {
    ……;
}
```








## 相关信息


### 手动登录错误码


手动登录的错误码通过[`onFailed`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1_request_callback.html#a366e1b9cb6cf0d11355c28f3fc694b69)回调返回，具体如下：


错误码 | 说明 
:-------- | :-------- 
302 | App Key、`accid`和`token`三者不对应 
408 | 连接超时
415 | 网络断开或者连接云信服务端失败 
416 | 调用频次过高 
1000 | 本地数据库未打开。请在手动登录成功后打开本地数据库 



### <span id="断网重连">断网重连机制</span>

SDK 提供了自动重连机制（自动重新建立与云信服务端的连接并重新登录），所有重连的登录状态变更都会在[`observeOnlineStatus`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service_observer.html#adf734324bdc99f79b88aaba8899e76ab)方法中回调。

SDK 在两种场景下会自动进行重连：

- 手动/自动登录成功后，网络不佳导致连接断开的情况。
- 网络不佳时，账号密码本身正常（未被[封禁](https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUzOTA4NTY?platformId=60353#封禁账号)，且账号密码均正确），启动应用时调用自动登录接口的情况。

满足上述中一个条件，当用户遇到普通网络问题如连接超时等，会自动进行重连登录，**不需要上层开发者去做额外的重登逻辑**。


### 多端登录与互踢

当前 NIM SDK 支持配置四种不同的 IM 多端登录与互踢策略，具体参见[多端登录与互踢](https://doc.yunxin.163.com/messaging/guide/jY2MDg0OTQ?platform=android)。



### 离线查看数据

对于一些弱 IM 场景，需要在登录成功前或者未登录状态下访问指定账号的数据（聊天记录、好友资料等）。

SDK 提供两种方案：

- 使用[自动登录](#自动登录)。在登录成功前，可以访问 SDK 服务来读取本地数据（但不能发送数据）。

- 在手动登录成功前（可能由于网络问题，登录时间较长），调用[`AuthService#openLocalCache`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#a7ceb17740700c62916ce72feb38e9b29)方法在离线时打开本地数据。这是一个同步方法，打开后即可读取 SDK 数据库中的记录。可以通过[注销](https://doc.yunxin.163.com/messaging/guide/TAyOTEyMTk?platform=android)来切换账号查看本地数据。



### 登录状态转换流程

<img style="width:70%" src="https://yx-web-nosdn.netease.im/common/16d74de1533c538563bd958877956ccd/Android登录状态转换简图.png"/>


<div style="width:170px">登录状态（StatusCode）</div>    | 说明 
:------- | :-------
`INVALID` | 未定义 
`UNLOGIN` | 未登录/登录失败。登录成功之后，如果触发了 `UNLOGIN` 回调，不需要尝试重新手动登录，SDK 内部有自动重连逻辑
`NET_BROKEN` | 网络连接已断开 
`CONNECTING` | 正在连接云信服务端 
`LOGINING` | 正在登录中 
`SYNCING` | 正在同步数据，登录成功后开始同步
`LOGINED` | 已成功登录 
`KICKOUT` | 被其他端的登录踢下线，此时应该跳转至手动登录界面。具体机制参见<a href="https://doc.yunxin.163.com/docs/TM5MzM5Njk/zcwNjEyNjg?platformId=60002" target="_blank">多端登录与互踢策略</a>。被踢后，**无法自动登录**
`KICK_BY_OTHER_CLIENT` | 被同时在线的其他端主动踢下线（通过<a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#a27bbb08421c17476cf6faeee95cde8eb" target="_blank">`kickOtherClient`</a>方法），此时应该跳转至手动登录界面。被踢后，**无法自动登录**
`FORBIDDEN` | 被服务器禁止登录（<a href="https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUzOTA4NTY?platformId=60353#封禁账号" target="_blank">云信 IM 账号被禁用</a>）。被禁止登录后，**无法自动登录**
`VER_ERROR` | SDK 版本错误。出现该登录异常后，**无法自动登录**
`PWD_ERROR` | 云信 IM 账号（accid）或 Token 错误。出现该登录异常后，**无法自动登录**
`DATA_UPGRADE` | 数据库需要迁移到加密状态（类似被踢出、<a href="https://doc.yunxin.163.com/docs/TM5MzM5Njk/TUzOTA4NTY?platformId=60353#封禁账号" target="_blank">云信 IM 账号被禁用</a>、Token 错误等情况。如自动登录失败，需要返回到登录界面进行重新登录操作）


## 常见问题

### 手动登录和自动登录的主要区别是什么？


手动登录和自动登录主要在于：

<div style="width:100px">差异点</div> | 说明 
---- | --------------
NIM SDK 是否接管登录失败后的处理 | <ul><li>手动登录：NIM SDK 认为手动登录即是终端用户发起登录的流程，因此在登录失败后（如网络情况不佳、密码错误），NIM SDK 会触发相应回调，并停止重连操作，等待用户再次发起登录操作</li><li>自动登录：自动登录失败后仍旧尝试重连，直到登录成功为止（密码错误等情况除外）</li></ul>
云信服务端是否验证当前登录设备的安全性 | <ul><li>手动登录：不验证</li><li>自动登录：自动登录时，如果当前登录设备不是上一次登录设备，云信服务端会自动禁止其登录，以保证安全性。</li></ul>

::: note note
如您选择自动登录，当您的应用在后台被唤起时，会计算为1次登录行为，计入日活统计作为计费依据。
:::

### 断线后是否会自动重连？

一旦登录成功后（或者调用过自动登录），NIM SDK 将接管所有的重连情况：在网络正常的情况下不停重试重连直到正常登录为止，并不需要做额外的登录操作（聊天室同理）。

### 如何根据产品形态选择 IM 登录方式？

接入网易云信 IM 服务的产品大致分为两种形态：

- IM 产品：通讯作为其核心模块。典型例子如微信、易信、网络直播相关应用。
- 非 IM 产品：通讯只是其附带模块，典型例子如各种有私信模块的应用。

对于 IM 产品，由于通讯能力是核心能力，如果云信无法登录成功则整个应用将无法正常表现，所以推荐在执行业务逻辑前，首先完成应用服务端和云信服务端的登录。只有应用服务端和云信服务端都登录成功才认为整个登录完成。而对于非 IM 产品而言，通讯能力是可以在登录应用服务端成功后延迟加载，登录成功拿到服务端下发的云信 IM 账号和 `token` 后进行自动登录即可。


### 如何获取云信服务端当前时间？

可调用[`MiscService#getServerTime`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1misc_1_1_misc_service.html#a2c20f10994c4d737e0264a6a7dddbdbe)方法获取云信服务端当前的时间戳。该方法的调用有频控限制。如果处于频控限制内，返回的时间为上一次获取时间 + 两次时间的偏移量。



### 如何处理登录请求被拒绝问题？

若您开启了应用标识安全验证，需要在将列表中写入允许的客户端应用标识。当请求登录的客户端应用标识不在列表中时，登录请求将被拒绝。

在控制台首页**应用管理**选择应用进入**应用配置**页面，顶部选择**标识管理**页签，添加对应的客户端应用标识。


![应用标识管理.png](https://yx-web-nosdn.netease.im/common/da2de7d1dfb244f321bcc582843ac26d/应用标识管理.png)


