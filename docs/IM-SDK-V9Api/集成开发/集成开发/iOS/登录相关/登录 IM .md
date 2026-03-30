
完成 NIM SDK 的初始化之后，用户需要先调用 SDK 的登录接口登录 IM。登录成功后，用户才能正常调用消息和会话等其他 SDK 接口。

本文介绍账号集成与登录的技术原理、实现 IM 登录的流程、IM 登录状态转换流程，以及[相关常见问题](#常见问题)。


## 技术原理






<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/f7d332058c2fed770bc0691fb3a2dd18/账号集成与登录原理新图.png" />



IM 的登录与账号集成密切相关。上图展示了应用集成 NIM SDK 后，从账号集成到登录 IM 成功的主要流程：

1. 用户在应用客户端注册用户账号时，由应用服务端向云信服务端发起[创建 IM 帐号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)的请求。
2. IM 帐号创建成功后，云信服务端会返回该 IM 帐号(即 `accid` )和 `token` 等信息。此时，应用服务端需要负责保存 `accid` 和 `token` 的映射关系。
3. 应用客户端发起登录请求时，先走应用自有的登录验证逻辑，如帐号和密码的验证。
4. 验证成功后，应用服务端将与该用户对应的 `accid` 和 `token` 等信息返回给应用客户端。此时，应用客户端需要负责保存 `accid` 和 `token` 的映射关系。
5. 当应用客户端需要调用云信的 IM 服务时，需要先进行 `token` 验证，以登录 IM 服务。
6. `token` 验证成功后，应用客户端登录 IM 服务成功。之后用户便可调用 NIM SDK 的相关接口使用 IM 服务，如进行 IM 消息收发。

::: note note
- 终端用户使用云信 IM 服务时，应用本身的用户帐号和云信的 IM 账号（`accid`）**彼此独立**。云信的 IM 账号只用于云信 IM 服务的鉴权，**IM 账号并不等同于应用的用户账号**。
- 应用的用户帐号和密码，与云信登录 IM 使用的 `accid` 和 `token` 完全不一致。`accid` 和 `token` 不由终端用户创建，而是由应用服务端分配，以保证安全性。
:::




## 前提条件

实现登录 IM 前，请确保已：

- 已完成[初始化](https://doc.yunxin.163.com/messaging/guide/TE0MDc5MTI?platform=iOS)。

- 已在云信控制台配置应用的 [IM 登录策略](https://doc.yunxin.163.com/messaging/guide/jQ3NDM5Mzk?platform=iOS#控制台配置)。如未配置相应的登录策略，可能导致后续调用登录接口时因无登录权限而报错（状态码：403）。
- （可选）已在控制台[配置客户端应用标识](https://doc.yunxin.163.com/console/docs/jU3MDY4Njk?platform=console#配置客户端应用标识)。



## 实现登录 IM





### 步骤1：准备 Token


登录 IM 需要通过`token`进行鉴权。云信提供静态和动态这两种 `token` 类型，您可根据业务需求进行选择。

- 静态`token`：默认为永久有效。如有需要，可通过云信服务端 API [主动刷新 Token](https://doc.yunxin.163.com/messaging/guide/DUxNDQ3NjA?platform=server)。


- 动态`token`：具备时效性，可在生成时设置`token`的有效期。


#### **获取静态Token**

- 方式1：在控制台获取静态 Token

    如果您只需要进行简单的**体验或者快速测试**，那么可以在云信控制台创建测试用的 IM 账号，并获取与该 IM 账号相应的**静态`token`**。具体参见[注册调试用的 IM 账号](https://doc.yunxin.163.com/messaging/guide/TE2Nzg1MDg?platform=iOS#4-注册-im-账号)。获取的静态token可用于下文提及的[静态 Token 登录](#静态Token登录)的鉴权。


- 方式2：调用服务端 API 获取静态 Token


    如果您有正式的**生产环境**，且您的业务**仅需保障基础的用户信息安全**，那么需要通过云信 IM 服务端 API 注册 IM 账号，并获取与之相对应的**静态`token`**。具体参见[注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)。获取的静态`token`可用于[静态 Token 登录](#静态Token登录)的鉴权



#### **获取动态Token**

如果您有正式的**生产环境**，且您的业务**对用户信息安全有较高的要求**，可使用动态 `token`。动态 token 可用于[动态 Token 登录](#动态Token登录)的鉴权。

1. [注册云信 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server)，获取 IM 账号（`accid`）和静态 `token`。

2. 基于App Key、App Secret 和 `accid`，通过[约定算法](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)在应用服务端生成**动态`token`**。

3. 客户端可通过在初始化时实现 `dynamicTokenForAccount:` 方法，从回调中获取动态 `token`。



#### **获取动态LoginExt**

NIM SDK 也支持获取动态的登录自定义扩展字段 `loginExt`。动态 `loginExt` 适用于所有登录模式，其中，在第三方回调登录模式中使用动态 `loginExt`时，第三方服务器可以使用该字段来进行鉴权。

客户端可通过在初始化时实现 `dynamicLoginExtForAccount:` 方法，从回调中获取动态 `loginExt`。




### 步骤2：注册相关监听


调用登录接口前，需要先实现监听 IM 登录状态、自动登录失败事件以及数据库开启事件。

#### 监听登录状态

注册[`onLogin:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#a70055366358595d63b0e1c07aedeb55f)回调，监听登录状态（`NIMLoginStep`）。该回调主要用于客户端 UI 刷新。

<details><summary><b>点击查看 NIMLoginStep 枚举列表</b></summary>
NIMLoginStep 枚举列表

| 枚举值               | 说明                 |
|----------------------|----------------------|
| `NIMLoginStepLinking`  | 连接服务器  |
| `NIMLoginStepLinkOK`   | 连接服务器成功 |
| `NIMLoginStepLinkFailed`  | 连接服务器失败 |
| `NIMLoginStepLogining`  | 登录 |
| `NIMLoginStepLoginOK`   | 登录成功 |
| `NIMLoginStepLoginFailed`  | 登录失败 |
| `NIMLoginStepSyncing`  | 开始同步数据 |
| `NIMLoginStepSyncOK`   | 同步数据完成 |
| `NIMLoginStepLoseConnection`  | 连接断开 |
| `NIMLoginStepNetChanged`  | 网络切换 |

一次完整的登录状态变化的基本流程（不包含断网重连）如下： 

  1.  `NIMLoginStepLinking` 
  2. `NIMLoginStepLinkOK` 
  3. `NIMLoginStepLogining`
  4. `NIMLoginStepLoginOK` 
  5. `NIMLoginStepSyncing`
  6. `NIMLoginStepSyncOK`


<note type=note>涉及断网重连的登录状态转换流程，参见下文的<a href="#登录状态转换流程">登录状态转换流程</a>。 </note>


</details>




NIM SDK 在登录成功后，会自动同步群信息，离线消息，漫游消息，系统通知等数据。数据同步过程对应`NIMLoginStep`枚举里的：
- `NIMLoginStepSyncing`：开始同步数据。
- `NIMLoginStepSyncOK`：同步数据完成。





::: note note
在数据同步完成后，<b>整个登录过程才算真正完成</b>。
:::

<br>

示例代码如下：

```
@interface Clazz: NSObject <NIMLoginManagerDelegate>
@end

@implementation Clazz
- (instancetype)init
{
    self = [super init];
    if (self) {
        [[[NIMSDK sharedSDK] loginManager] addDelegate:self];
    }
    return self;
}

- (void)dealloc
{
    // 当前对象释放时取消注册回调，避免泄露
    [[NIMSDK sharedSDK].loginManager removeDelegate:self];
}

// 监听登录进度
- (void)onLogin:(NIMLoginStep)step
{
    // your code
}

@end
```


#### 监听自动登录失败事件



如果后续需实现 IM 自动登录，还需注册[`onAutoLoginFailed:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#ab96ef125e18a7722668b30ddd0289e7f)回调，监听自动登录失败事件。一些特殊的登录错误需要通过该回调返回，包括 App Key 未设置、参数错误、密码错误、多端登录冲突、[账号被封禁](https://doc.yunxin.163.com/messaging/guide/TUzOTA4NTY?platform=server)、操作过于频繁等，建议在集成时能尽可能在上层应用考虑应对逻辑。

例如，自动登录时如果用户名和密码不匹配，上层应用需实现**登出并提示用户手动登录**或是**从应用服务器刷新相应的用户名和密码**等逻辑。


::: note note 
网络状态较差时容易导致自动登录发生网络超时错误，此时上层应用无需处理，SDK 会持续有策略地重连。
:::


#### 监听数据准备完成事件

发送消息等后续操作要求数据库处于开启状态，否则可能导致发送消息失败，或者阻塞等待数据库开启。

当手动登录或自动登录成功后，云信 IM 开始打开数据库，调用 `onDataReady` 方法注册观察者，监听数据库成功开启的回调。

首次登录成功后开启数据库会回调，不登出再调用登录不会多次回调。



### 步骤3：登录 IM




#### <span id="登录方式概览">登录方式概览</span>




NIM SDK 登录方式分为两大类，即手动登录和自动登录。其中手动登录可进一步分为静态`token`登录、动态`token`登录和通过第三方回调登录。 

您可按需实现**一种或多种**手动登录方式，并**在手动登录成功后**，实现自动登录。 


<div style="width:100px">登录方式</div> | 子方式 | 鉴权方式 | 使用场景
---- | -------------- | ---------
手动登录 |  [静态 Token 登录](#静态Token登录)  | [静态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#静态token鉴权)  | 如下登录场景，用户需要手动登录 IM：<ul><li>在新设备上首次登录 IM</li><li>被同时在线的[其他设备踢下线](https://doc.yunxin.163.com/messaging/guide/jI1MzcwNTQ?platform=iOS)后再次登录 IM</li><li>切换 IM 账号后再次登录 IM</li><li>[注销登录](https://doc.yunxin.163.com/messaging/guide/TMyNTU4MjY?platform=iOS)后再次登录 IM</li></ul>
^^ | [动态 Token 登录](#动态Token登录)    | [动态 Token 鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权) |  ^^
^^   |   [通过第三方回调登录](#通过第三方回调登录)   |  [通过第三方回调鉴权](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#基于第三方回调的鉴权)  | ^^
[自动登录](#自动登录)   |  继承手动登录的方式  |   继承手动登录的鉴权方式    |  应用被清理后，用户再次点击应用图标启动应用时，无需输入用户名和密码即可完成登录的场景。**自动登录需在手动登录成功后使用**     

::: note note 
**推荐**在手动登录成功后，将`accid`和`token`**保存到本地**，方便下次应用启动自动登录时使用。如果登录失败，清除本地保存的用户登录信息，防止下次启动走自动登录逻辑。更多相关说明，参见[IM 登录最佳实践](https://doc.yunxin.163.com/messaging/guide/Tg0MjYxODg?platform=iOS)。您也可以参考该文档中提供的 **Sample Code** 实现 IM 登录。
:::



  


#### <span id="手动登录">方式1：手动登录</span>

手动登录对应用户手动输入登录账号密码的场景。

##### <span id="静态Token登录">**静态 Token 登录**</span>




调用[`login:token:authType:loginExt:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7dedc10fcbadf36fb66ce9cc9710b8f6)方法进行手动登录。


参数| 类型|  是否必传| 说明
---- | -------------- | ---| ------
`account` | NSString  | 是| 用户的 IM 账号（即 `accid`）
`token` | NSString | 是 | 获取到的静态 `token`   
`authType` | int |否| 登录 IM 的鉴权方式。采用静态 `token` 登录时，使用**默认的 0** 即可
`loginExt` |NSString | 否 | 登录自定义扩展字段，长度上限为 1k 字符。若在初始化时实现了 `dynamicLoginExtForAccount:` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先取返回值，忽略此处输入的 loginExt 值。

示例代码如下：

```
/**
 * 静态token的模式登录IM
 *
 * @param account 账号
 * @param token 静态Token
 */
- (void) loginByStaticToken:(NSString *)account token:(NSString *)token
{
    // 静态token鉴权
    [[[NIMSDK sharedSDK] loginManager] login:account token:token authType:NIMSDKAuthTypeDefault loginExt:@"" completion:^(NSError *error)
    {
        if (error == nil) {
            // 登录成功
            // your code
        } else {
            // 登录失败
            // your code            
        }
    }];
}
```

上述示例代码中的`error`为登录错误信息，登录成功则为 nil。

##### <span id="动态Token登录">**动态 Token 登录**</span>

NIM SDK 支持动态 `token` 登录这一登录方式。该登录方式的 `token` 具备时效性，可有效提升 `token` 破解难度，降低密码泄露风险。

要实现动态登录 IM，需完成如下两步操作：

1. 初始化时，实现 `NIMSDKConfigDelegate` 中的 `dynamicTokenForAccount:` 方法获取上文提及的[基于App Secret生成的动态Token](#获取动态token)。


2. 调用[`login:token:authType:loginExt:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7dedc10fcbadf36fb66ce9cc9710b8f6)方法进行动态登录，调用时需**将`authType`设置为 1**。


    具体参数说明如下：



    <div style="width:120px">参数</div> | <div style="width:80px">类型</div> | 是否必传 | 说明
    ---- | -------| ------- | ---------
    `account` | NSString | 是 | 用户的 IM 账号，即`accid`
    `authType` | int | 该登录方式必传   |**采用动态`token`登录时必须传入 1**，表示通过动态`token`鉴权，动态`token`[基于 App Secret 计算生成](https://doc.yunxin.163.com/messaging/guide/zE2NzA3Mjc?platform=server#动态token鉴权)
    `token` | NSString | 否 | 静态 `token`。当 IM 采用动态 `token` 鉴权方式且在初始化时实现了 `dynamicTokenForAccount:` 方法，回调该方法时返回了非空的 token 值，那么优先使用返回的动态 token 进行鉴权；如果回调返回空值，会返回错误码，此时若已传入静态 token，则取此处的静态 token 进行鉴权；如果回调返回空值且未传入静态 token，则直接返回 414 错误码<note type=notice>如果您的应用启用了云信的聊天室功能，并且采用**非独立模式&静态 token 登录方式**鉴权时，那么此处必须传入静态 token。传入后，后续**非独立模式的聊天室静态登录**时会使用该静态 token</note>
    `loginExt` |NSString | 否 | 登录自定义扩展字段，长度上限为 1k 字符。若在初始化时实现了 `dynamicLoginExtForAccount:` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先取回调返回值，忽略此处输入的 loginExt 值

    :::note notice
    - 使用动态 token 登录（即登录方式 authType 为 1）时，如果注册了动态 token 回调，但返回空值且未传入静态 token（可能第三方服务器设置了动态时间），则直接返回 414 错误码，云信内部不做登录请求。
    - 若注册了回调，回调返回空值，但是登录信息中已传入静态 token，也会返回相关错误码，但是此时，不中断重连，即继续走重连机制（若在初始化设置了自动重连的次数限制，注意该场景下的自动重连次数不计入），等待动态 Token 的传入。
    :::

    **示例代码如下**：

    ```
    @interface NTESAppDelegate ()
    @property (nonatomic, strong) id<NIMSDKConfigDelegate> sdkConfigDelegate;
    @end

    @implementation NTESAppDelegate
    // 设置云信SDK
    - (void)setupNIMSDK
    {    
        self.sdkConfigDelegate = [[NTESSDKConfigDelegate alloc] init];
        [[NIMSDKConfig sharedConfig] setDelegate:self.sdkConfigDelegate];
        
        // your code
    }

    @end

    @implementation NTESSDKConfigDelegate
    - (NSString *)dynamicTokenForAccount:(NSString *)account {
        // 在这里返回你的动态Token
        return "your dynamic token";
    }
    @end

    /**
    * 动态token的模式登录IM
    *
    * @param account 账号
    */
    - (void) loginByDynamicToken:(NSString *)account
    {
        // 动态token鉴权，此时不需要传入token，SDK会通过NIMSDKConfigDelegate回调dynamicTokenForAccount获取Token
        [[[NIMSDK sharedSDK] loginManager] login:account token:@"" authType:NIMSDKAuthTypeDynamicToken loginExt:@"" completion:^(NSError *error)
        {
            // your code
        }];
    }
    ```



##### <span id="通过第三方回调登录">**通过第三方回调登录**</span>




如采用该登录方式，**云信服务端不做 IM 登录鉴权**，鉴权工作需由指定的第三方服务器（可以是应用服务器）进行。

1. 实现该登录方式，需提前[开通和配置第三方服务](https://doc.yunxin.163.com/messaging/guide/jI3ODc2ODE?platform=server#开通和配置第三方服务)。

2. 若您的应用需要采用第三方服务器的动态 Token 或者动态 LoginExt 鉴权，那么需要在初始化时实现 `NIMSDKConfigDelegate` 中的 `dynamicLoginForAccount:` 和 `dynamicLoginExtForAccount:` 方法，SDK 会在登录过程时动态通过 Delegate 方法获取第三方回调的动态 Token 和动态扩展字段（`loginExt`）。

   示例代码如下：
   ```
    @interface NTESAppDelegate ()
    @property (nonatomic, strong) id<NIMSDKConfigDelegate> sdkConfigDelegate;
    @end

    @implementation NTESAppDelegate
    // 设置云信SDK
    - (void)setupNIMSDK
    {    
        self.sdkConfigDelegate = [[NTESSDKConfigDelegate alloc] init];
        [[NIMSDKConfig sharedConfig] setDelegate:self.sdkConfigDelegate];
        
        // your code
    }
    @end

    @implementation NTESSDKConfigDelegate
    - (NSString *)dynamicTokenForAccount:(NSString *)account {
        // 在这里返回你的动态Token
        return "your dynamic token";
    }

    - (NSString *)dynamicLoginExtForAccount:(NSString *)account {
        // 在这里返回你的动态LoginExt
        return "your dynamic loginExt";
    }
    @end
   ``` 

3. 调用[`login:token:authType:loginExt:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7dedc10fcbadf36fb66ce9cc9710b8f6)方法进行手动登录，调用时需**将`authType`设置为 2**。


    具体参数说明如下：


    <div style="width:120px">参数</div> | <div style="width:80px">类型</div> | 是否必传 | 说明
    ---- | -------| ------- | ---------
    `account` | NSString | 是 | 用户的 IM 账号，即`accid`
    `authType` | int | 该登录方式必传   |**采用该登录方式时必须传入 2**，表示通过第三方回调进行鉴权
    `loginExt` |NSString | 否 | 登录自定义扩展字段，长度上限为 1k 字符。第三方服务器可以使用该字段来鉴权。若在初始化时实现了 `dynamicLoginExtForAccount:` 方法，并且回调该方法时返回了非空的 loginExt 值，则优先使用返回的第三方动态 loginExt 值进行鉴权，若回调返回空值，会返回错误码，如果此时已传入静态 loginExt，则取此处手动传入的 loginExt 进行鉴权。
    `token` | NSString | 否 | 静态 `token`。当 IM 采用第三方回调鉴权方式且在初始化时实现了 `dynamicTokenForAccount:` 方法，回调该方法时返回了非空的 token 值，那么优先使用返回的第三方动态 token 进行鉴权；若回调返回空值，会返回错误码，如果此时已传入静态 token，则取此处的静态 token 进行鉴权<note type=notice>如果您的应用启用了云信的聊天室功能，并且采用**非独立模式&静态 token 登录方式**鉴权时，那么此处必须传入静态 token。传入后，后续**非独立模式的聊天室静态登录**时会使用该静态 token</note>

    :::note notice
    - 使用第三方回调登录（即登录方式 authType 为 2）时，如果注册了第三方动态 token 和 loginExt 回调，但都返回空值且未传入静态 token 和 loginExt（可能第三方服务器设置了动态时间），则直接返回 414 错误码，云信内部不做登录请求。
    - 若注册了回调，回调返回空值，但是登录信息中已传入静态鉴权字段，也会返回相关错误码，但是此时，不中断重连，即继续走重连机制（若在初始化设置了自动重连的次数限制，注意该场景下的自动重连次数不计入），等待第三方动态 Token 或 loginExt 的传入。
    :::

    **示例代码如下**：


    ```
    /**
    * 第三方鉴权的模式登录IM
    *
    * @param account 账号
    * @param token 登录Token，透传给第三方服务器完成鉴权。如果您已经设置了NIMSDKConfigDelegate，并且实现了dynamicTokenForAccount，此处无需传入静态Token
    * @param loginExt 登录扩展字段，透传给第三方服务器完成鉴权。如果您已经设置了NIMSDKConfigDelegate，并且实现了dynamicLoginExtForAccount，此处无需传入静态LoginExt
    */
    - (void) loginByDynamicToken:(NSString *)account token:loginToken loginExt:loginExt
        [[[NIMSDK sharedSDK] loginManager] login:loginAccount
                                            token:loginToken
                                            authType:NIMSDKAuthTypeThirdParty
                                            loginExt:loginExt
                                        completion:^(NSError *error) {
                                            // your code
                                        }    
    ```


4. 发起[登录相关回调](https://doc.yunxin.163.com/messaging/guide/jc3MzA5NTk?platform=server)的请求，由第三方服务器进行鉴权并判定 IM 登录事件是否放行通过。

    若不通过，云信服务端将返回 302 错误码。








#### <span id="自动登录">方式2：自动登录</span>

手动登录成功且将`accid`和`token`保存至本地后，可调用[`autoLogin:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7239363d8c7d432e68261094b23081b7)方法进行自动登录。

自动登录一般用于应用被清理后，用户再次点击应用图标启动应用，无需输入用户名和密码即可完成登录的场景。此时应用可以在无网络、未登录成功的状态下直接访问用户本地 SDK 数据。


| <div style="width:90px">参数</div>       | <div style="width:90px">类型</div>  | 是否必传 | 说明       |
| ---------- | -------- | --------------------------- |
| `account`    | NSString |是 | 从本地获取到的 IM 账号（即`accid`）   |
| `token`      | NSString | 是| 从本地获取到的`token` |
| `forcedMode` | BOOL     | 否 | 强制模式开关<ul><li>默认为 NO，非强制模式。非强制模式下的自动登录，服务器将检查当前登录设备是否为上一次登录设备，如果不是，服务器将拒绝这次自动登录(返回 error code 为 417 的错误)</li><li>若设置为 YES， 强制模式，那么自动登录时云信服务端将<b>不检查</b>当前登录设备是否为上一次登录设备，<b>安全性较低</b>，但较为便捷</li></ul>                |


::: note note
**推荐**参考[自动登录最佳实践](https://doc.yunxin.163.com/messaging/guide/Tg0MjYxODg?platform=iOS#自动登录)和[登录状态处理最佳实践](https://doc.yunxin.163.com/messaging/guide/Tg0MjYxODg?platform=iOS#登录状态处理)实现自动登录以及相应的登录状态处理逻辑。
:::

<br>

示例代码如下：

```objc
NIMAutoLoginData *loginData = [[NIMAutoLoginData alloc] init];
loginData.account = account;
loginData.token = token;

[[[NIMSDK sharedSDK] loginManager] autoLogin:loginData];
```




### 步骤4（可选）：主动查询登录状态

调用[`isLogined`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a94179d558b63663a2390aa2a74b50bda)方法主动查询当前 IM 账号是否已处于在线状态。







## 相关信息


### <span id="断网重连">断网重连</span>

SDK 提供了自动重连机制（自动重新建立与网易云信服务器的连接并重新登录），所有重连的登录状态都会在 [`onLogin:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#a70055366358595d63b0e1c07aedeb55f) 方法中回调，涉及断网重连的登录状态转换流程，参见下文的[登录状态转换流程](#登录状态转换流程)。

SDK 在两种场景下会自动进行重连：

- 手动或自动登录成功后，网络不佳导致 SDK 与云信服务端连接断开的情况。
- 网络不佳时，账号和密码本身正常（未[被封禁](https://doc.yunxin.163.com/messaging/guide/TUzOTA4NTY?platform=server)，且账号、密码均正确），启动应用时调用自动登录接口的情况。


满足上述中一个条件，当用户遇到普通网络问题如连接超时等，SDK 都会自动进行重连登录，**不需要上层开发者去做额外的重登逻辑**。


::: note notice
重试次数超过预定上限时，SDK 不会继续重连。重试次数（[`maxAutoLoginRetryTimes`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d6/d13/interface_n_i_m_s_d_k_config.html#a0b54c6303a902cb51419170b06375612)）在 `NIMSDKConfig` 中定义，**默认无重试次数限制**，需在[初始化](https://doc.yunxin.163.com/messaging/guide/TE0MDc5MTI?platform=iOS)时配置。
:::


### 多端登录与互踢

当前 NIM SDK 支持配置四种不同的 IM 多端登录与互踢策略，具体参见[多端登录与互踢](https://doc.yunxin.163.com/messaging/guide/jI1MzcwNTQ?platform=iOS)。



### 登录状态转换流程


下图中，深蓝色元素代表登录状态，浅绿色元素代表手动登录或自动登录。

![IMiOS登录状态转换简图.png](https://yx-web-nosdn.netease.im/common/b462039d6d67cca143d5537ce9532494/IMiOS登录状态转换简图.png)

### 相关辅助方法


`NIMLoginManager`协议中提供了辅助方法：



方法| 说明
---- | -------------- 
[`currentAccount`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#aca722d98fdda2e28e877a8aabfb86afa)  | 获取当前登录的 IM 账号。如果没有登录成功，会返回空字符串""
[`queryServerTimeCompletion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#ac8328f917e2e3e6eba21687f59af0858) | 查询云信服务端当前的时间。该方法有调用频控，当调用失败时默认返回上一次调用成功时返回的时间


## 常见问题

### 手动登录和自动登录的主要区别是什么？


<div style="width:100px">差异点</div> | 说明 
---- | --------------
NIM SDK 是否接管登录失败后的处理 | <ul><li>手动登录：NIM SDK 认为手动登录即是终端用户发起登录的流程，因此在登录失败后（如网络情况不佳、密码错误），NIM SDK 会触发相应回调，并停止重连操作，等待用户再次发起登录操作</li><li>自动登录：自动登录失败后仍旧尝试重连，直到登录成功为止（密码错误等情况除外）</li></ul>
云信服务端是否验证当前登录设备的安全性 | <ul><li>手动登录：不验证</li><li>自动登录：自动登录时，如果当前登录设备不是上一次登录设备，云信服务端会自动禁止其登录，以保证安全性。<br>您也可设置自动登录为强制登录（通过自动登录接口的`forcedMode`参数），以忽略安全性检查。这种做法比较适合非 IM 产品延迟加载通讯模块的场景：通过服务端下发的正确的 IM 账号 直接进行自动登录，无需关心任何登录出错的情况</li></ul>

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

### 如何处理登录请求被拒绝问题？

若您开启了应用标识安全验证，需要在将列表中写入允许的客户端应用标识。当请求登录的客户端应用标识不在列表中时，登录请求将被拒绝。

在控制台首页**应用管理**选择应用进入**应用配置**页面，顶部选择**标识管理**页签，添加对应的客户端应用标识。


![应用标识管理.png](https://yx-web-nosdn.netease.im/common/da2de7d1dfb244f321bcc582843ac26d/应用标识管理.png)
