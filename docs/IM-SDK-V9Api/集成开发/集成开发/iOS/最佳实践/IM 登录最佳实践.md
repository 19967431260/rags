登录对于 IM 产品来说至关重要，是后续业务顺利进行的前提条件。开发者集成 NIM SDK 的各项能力时，如果未能正确使用登录接口或处理登录状态，将引发不必要的问题，影响开发进度。本文介绍如何以最佳姿势进行**手动登录**和**自动登录**，进而实现 IM 登录。


- 手动登录：首次登录 IM 时调用`NIMLoginManager.login:token:completion:`方法实现。
- 自动登录：手动登录 IM 成功之后调用`autoLogin:token:`。调用时机为：手动登陆成功之后下次启动应用时；自动登录之后的应用存活期间，因为网络断开 SDK 会自己重连，不需要业务层调用。


::: note note
本文的手动登录**仅以静态 Token 登录为例**，更多登录相关说明请参见[登录 IM](https://doc.yunxin.163.com/messaging/guide/TU3MTM2ODM?platform=iOS)。
:::



## 前提条件

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[集成 NIM SDK](https://doc.yunxin.163.com/messaging/guide/TA1MzA2Njg?platform=iOS#步骤-1集成-sdk)。
- 已通过云信服务端[注册 IM 账号](https://doc.yunxin.163.com/messaging/guide/DQ3Nzk1MTY?platform=server) ，获取 IM 账号（`accid`）和对应的静态`token`。

    您也可通过控制台注册 IM 测试账号。测试账号及对应的`token`仅适用于调试环境，线上生产环境必须将测试账号及其`token`替换为云信服务端生成的正式`accid`和`token`。

## 实现方案


### **手动登录**


IM 手动登录接口的调用，对应用户手动输入账号和密码进行登录的场景。一般情况下，该接口需在应用的`didFinishLaunchingWithOptions`启动后，用户在登录界面点击登录时调用。其他情况一般不需要调用手动登录接口，除非是账号被踢下线、切换账号、注销登录后重新登录等情况。在登录界面中，IM 登录可以作为整个应用登录过程的一个环节。常见的方案是先实现应用自身账号体系的登录，成功后再使用返回的`accid`和`token`进行 IM 的登录。



- **手动登录流程**

    <br>

    ![手动登录流程图.png](https://yx-web-nosdn.netease.im/common/5dfd8fc1ecda5fde88b261129b4c316a/手动登录流程图.png)



  
- **接口调用**

    1. 调用[`login:token:completion:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#af19374f0237b69dcb61b04499dcf1454)方法手动登录云信IM。
    
        可以在调用手动登录接口时，在登录界面加上等待加载框，等收到登录结果之后再隐藏该等待加载框。登录没有返回 error 就是登录成功。
        
    2. 调用后处理。
        - 如果登录成功，保存 IM 的`accid`和`token`到本地，方便下次应用启动自动登录时使用。
        - 如果登录失败，清理本地保存的用户登录信息，防止下次启动走自动登录逻辑。

    示例代码如下：

    ```
    [[[NIMSDK sharedSDK] loginManager] login:accid token:token completion:^(NSError * _Nullable error) {
                
                if (error) {
                    
                } else {
                    
                    [[NSUserDefaults standardUserDefaults] setObject:accid forKey:@"NIMAccid"];
                    [[NSUserDefaults standardUserDefaults] setObject:token forKey:@"NIMToken"];
                    
                    FirstViewController *mainTab = [[FirstViewController alloc] init];
                    [UIApplication sharedApplication].delegate.window.rootViewController = mainTab;
                }
            }];
    ```



### **自动登录**

手动登录 IM 成功后，下次启动应用可以使用云信 IM 的自动登录模式。自动登录后，即使登录未完成或者网络无法访问，应用也可以直接访问用户本地 SDK 数据。

自动登录主要针对应用被清理掉后，再次点击图标启动时，无需输入用户名和密码即可完成登录的场景。自动登录还有一个作用，即在网络不佳且账号和密码本身正常（未被封禁，且账号密码均正确）时，如果启动应用时调用手动登录接口未成功，SDK 会自动进行重连登录，不需要上层开发者去做额外的重登逻辑。


- **自动登录流程**

    <br>




    <img style="width:80%" src="https://yx-web-nosdn.netease.im/common/63944bd1fc6f3087a74074b7aa5123f9/自动登录流程图 iOS.png" />


- **接口调用**

    调用[`autoLogin:token:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a8c05c17ff5369ce9b70c6c7d33d6622e)或[`autoLogin:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7239363d8c7d432e68261094b23081b7)方法进行自动登录。一般在应用启动和初始化 SDK 之后，如果判断本地已经有持久化的账号和密码即可进行自动登录，自动登录没有回调结果，在跳转到应用首页之前调用一次即可。

    自动登录的**使用限制**如下：

    - 自动登录只能登录上次登录的IM 账号，不能登录其他账号。
    - 需要某个 IM 账号曾经通过手动登录接口登录成功后才可以调用。
    - 无论之前是否曾经手动登录成功，只要最近一次手动登录接口调用失败，则不可以继续自动登录。
    - 在被云信服务端踢下线、被同时在线的其他端踢下线、被[封禁账号](https://doc.yunxin.163.com/messaging/guide/TUzOTA4NTY?platform=server#封禁账号)、登录密码错误等情况下，后续自动登录将无效，需要用户通过手动登录接口重新登录。更多相关说明，见下文的[登录状态处理](#登录状态处理)。


    实现自动登录的示例代码如下（仅以`autoLogin:token:`的调用为例）：

    ```
    [[NIMSDK sharedSDK].loginManager addDelegate:self];
        NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];
        
        if ([[userDefaults objectForKey:@"NIMToken"] length] > 0) {
            //自动登录
            
            [[NIMSDK sharedSDK].loginManager autoLogin:[userDefaults objectForKey:@"NIMAccid"] token:[userDefaults objectForKey:@"NIMToken"]];
            
            FirstViewController *firstVc = [[FirstViewController alloc] init];
            UINavigationController *nav = [[UINavigationController alloc] initWithRootViewController:firstVc];
            firstVc.title = @"第一个页面";
            self.window.rootViewController = nav;
        } else {
            //登录
            LoginViewController *loginVc = [[LoginViewController alloc] init];
            UINavigationController *loginNav = [[UINavigationController alloc] initWithRootViewController:loginVc];
            loginVc.title = @"登录";
            self.window.rootViewController = loginNav;
        }

    ```

### **登录状态处理**


IM 登录状态表示当前登录的 NIM SDK 实例与云信服务端的长连接状态，也可以理解为用户设备和云信服务端的网络连接状态。


初始化 SDK 之后，可调用[`NIMLoginManager.addDelegate`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a049ec0b1a852feea6bcfd323858d7b8b)方法注册[`onLogin:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#a70055366358595d63b0e1c07aedeb55f)登录回调、[`onKickout:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#acd2ae586b5e4f0a9cec487727c164a63)被踢回调和[`onAutoLoginFailed:`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d5/dc6/protocol_n_i_m_login_manager_delegate-p.html#ab96ef125e18a7722668b30ddd0289e7f)自动登录失败回调，监听当前的登录状态，并通过 UI 层提示用户。其他使用场景一般只需要在手动登录成功后或者自动登录期间才需要处理 IM 登录状态。

::: note note 
登录的状态监听建议放在您应用的`AppDelegate`里。
:::

<br>

登录状态处理的流程图如下：


<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/2a7ae5f4dcffef678966cc8ad5fcf5ad/登录状态处理流程.png" />



示例代码如下：

:::::: div custom-tabs 
::: tab 监听登录状态

```
@interface AppDelegate ()<NIMLoginManagerDelegate>
@end
[[NIMSDK sharedSDK].loginManager addDelegate:self];
#pragma mark - 登录状态监听
- (void)onLogin:(NIMLoginStep)step {
    switch (step) {
        case NIMLoginStepLinking: {
            NSLog(@"---# 连接服务器ing");
            break;
        }
        case NIMLoginStepLinkOK: {
            NSLog(@"---# 连接服务器成功");
            break;
        }
        case NIMLoginStepLinkFailed: {
            NSLog(@"---# 连接服务器失败");
            break;
        }
        case NIMLoginStepLogining: {
            NSLog(@"---# 登录ing");
            break;
        }
        case NIMLoginStepLoginOK: {
            NSLog(@"---# 登录成功");
            break;
        }
        case NIMLoginStepLoginFailed: {
            NSLog(@"---# 登录失败");
            break;
        }
        case NIMLoginStepSyncing: {
            NSLog(@"---# 开始同步数据");
            break;
        }
        case NIMLoginStepSyncOK: {
            NSLog(@"---# 同步数据完成");
            break;
        }
        case NIMLoginStepLoseConnection: {
            NSLog(@"---# 连接断开");
            break;
        }
        case NIMLoginStepNetChanged: {
            NSLog(@"---# 网络切换");
            break;
        }
        case NIMLoginStepLogout: {
            NSLog(@"---# 登出");
            break;
        }
    }
}
```
:::

::: tab 监听被云信服务端或其他设备端踢下线

```
@interface AppDelegate ()<NIMLoginManagerDelegate>
@end
[[NIMSDK sharedSDK].loginManager addDelegate:self];
#pragma mark - 被踢(服务器/其他端)回调
- (void)onKickout:(NIMLoginKickoutResult *)result {
    //被踢的回调，有被踢的原因，需要在这里logout。
    [[NIMSDK sharedSDK].loginManager logout:^(NSError * _Nullable error) {
        //这里跳回登录页面
        
        self.window.rootViewController = [LoginViewController new];
        
        [[NSUserDefaults standardUserDefaults] setObject:@"" forKey:@"NIMAccid"];
        [[NSUserDefaults standardUserDefaults] setObject:@"" forKey:@"NIMToken"];
        
    }];
}
```

:::
::: tab 监听自动登录失败

```
@interface AppDelegate ()<NIMLoginManagerDelegate>
@end
[[NIMSDK sharedSDK].loginManager addDelegate:self];
#pragma mark - 自动登录失败
- (void)onAutoLoginFailed:(NSError *)error {
    //这里跳转到登录页面重新登录
    if (error) {
        self.window.rootViewController = [LoginViewController new];
    }
}
```

:::
::::::
  


## Sample Code 下载


<br>

<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="130px"  viewBox="-0.5 -0.5 195 115" style="background-color: rgb(255, 255, 255);"><defs><linearGradient x1="0%" y1="100%" x2="0%" y2="0%" id="mx-gradient-ffffff-1-2a6bf2-1-s-0"><stop offset="0%" style="stop-color: rgb(42, 107, 242); stop-opacity: 1;"/><stop offset="100%" style="stop-color: rgb(255, 255, 255); stop-opacity: 1;"/></linearGradient><style type="text/css">@import url(https://fonts.googleapis.com/css?family=Open+Sans);&#xa;</style></defs><g><a xlink:href="https://nim-nosdn.netease.im/MTAxMTAwMg==/bmltYV8zMDg0ODY1NDk0OF8xNjY5ODgxODM0ODM4XzM4NmVlMWE2LTgzZTAtNGFmMC05M2ZlLTc4NGE4ZjQ4YjJhYg==?createTime=1669881835316&download=aotoLogin.zip" target="_blank"><rect x="2" y="2" width="190" height="110" rx="30.8" ry="30.8" fill="#ffffff" stroke="#2a6bf2" stroke-width="5" pointer-events="all"/></a><a xlink:href="https://nim-nosdn.netease.im/MTAxMTAwMg==/bmltYV8zMDg0ODY1NDk0OF8xNjY5ODgxODM0ODM4XzM4NmVlMWE2LTgzZTAtNGFmMC05M2ZlLTc4NGE4ZjQ4YjJhYg==?createTime=1669881835316&download=aotoLogin.zip" target="_blank"><image x="80" y="11.5" width="33" height="33.86" xlink:href="data:image/png;base64,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"/></a><a xlink:href="https://nim-nosdn.netease.im/MTAxMTAwMg==/bmltYV8zMDg0ODY1NDk0OF8xNjY5ODgxODM0ODM4XzM4NmVlMWE2LTgzZTAtNGFmMC05M2ZlLTc4NGE4ZjQ4YjJhYg==?createTime=1669881835316&download=aotoLogin.zip" target="_blank"><rect x="37" y="62" width="142.5" height="30" fill="none" stroke="none" pointer-events="all"/><g transform="translate(-0.5 -0.5)"><switch><foreignObject pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility" style="overflow: visible; text-align: left;"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 141px; height: 1px; padding-top: 77px; margin-left: 38px;"><div data-drawio-colors="color: rgb(0, 0, 0); " style="box-sizing: border-box; font-size: 0px; text-align: center;"><div style="display: inline-block; font-size: 12px; font-family: &quot;Open Sans&quot;; color: rgb(0, 0, 0); line-height: 1.2; pointer-events: all; white-space: normal; overflow-wrap: normal;"><font color="#2a6bf2" size="1"><b style="font-size: 14px;"><span style="font-size: 20px;">点击下载 </span><br />Sample Code<br /></b></font></div></div></div></foreignObject><text x="108" y="81" fill="rgb(0, 0, 0)" font-family="Open Sans" font-size="12px" text-anchor="middle">点击下载...</text></switch></g></a><a xlink:href="https://nim-nosdn.netease.im/MTAxMTAwMg==/bmltYV8zMDg0ODY1NDk0OF8xNjY5ODgxODM0ODM4XzM4NmVlMWE2LTgzZTAtNGFmMC05M2ZlLTc4NGE4ZjQ4YjJhYg==?createTime=1669881835316&download=aotoLogin.zip" target="_blank"><path d="M 37.7 42.36 L 48.3 42.36 L 48.3 77.55 L 52.63 77.55 L 43 95.5 L 33.37 77.55 L 37.7 77.55 Z" fill="url(#mx-gradient-ffffff-1-2a6bf2-1-s-0)" stroke="none" pointer-events="all"/></a></g><switch><g requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"/><a transform="translate(0,-5)" xlink:href="https://www.diagrams.net/doc/faq/svg-export-text-problems" target="_blank"><text text-anchor="middle" font-size="10px" x="50%" y="100%">Text is not SVG - cannot display</text></a></switch></svg>



