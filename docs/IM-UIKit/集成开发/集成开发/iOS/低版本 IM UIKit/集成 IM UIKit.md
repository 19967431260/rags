<!--keywords: UIKit,IM,UI,UI组件库,UI界面,集成,SDK集成,新手 -->

云信 IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款即时通讯 UI 组件库，包括聊天、会话列表、通讯录、群管理等组件。

云信 IM UIKit 自 9.6.1 版本开始新增全新的[通用版 UI 组件](https://doc.yunxin.163.com/messaging-uikit/guide/TU0NTc4MjM?platform=iOS)，原有的 UI 组件（基础版）依旧保留，您可以根据需求自行选择基础版或通用版 UI 组件。

:::::: div custom-tabs
::: tab 基础版 UI
<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/11707474727796454a82bfdf823f5534/960主要模块.png" />
:::
::: tab 通用版 UI
<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/1d225879d3f6eda6e3a8027462f3dc60/960主要模块绿.png" />
:::
::::::


本文介绍如何快速跑通 IM UIKit 的集成流程。


## 前提条件

在开始集成 IM UIKit 前，请确保：
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/zQ3ODUyNjk?platform=iOS#4-注册-im-账号)，获取 accid 和 token。
- 已[获取示例项目](https://github.com/netease-kit/nim-uikit-ios)。
- 已准备如下开发环境/工具：
    - iOS 10.0 及以上版本
    - - Xcode 13.0 及以上版本

## 注意事项

由于 IM UIKit 的初始化与登录是通过底层调用 NIM SDK 接口来实现的，因此重复调用 IM UIKit 和 NIM SDK 的初始化与登录接口会相互覆盖传入的信息（包括**推送配置信息**）。

所以若用户同时集成 IM UIKit 和 NIM SDK，只需要调用一次初始化与登录接口即可。



## 实现流程

@startuml
!include https://raw.githubusercontent.com/bschwarz/puml-themes/master/themes/cerulean-outline/puml-theme-cerulean-outline.puml
(*) -right-> "按需导入组件"
-right-> "初始化"
-right-> "登录"
-right-> "初始化路由"
-right-> "页面搭建"
-right-> (*)
@enduml

### <span id="步骤1">步骤1：按需导入组件</div>

1. 根据业务需要，在 “Podfile” 文件中，以添加依赖的形式添加相应的 IM UIKit 组件。

    例如，需要会话聊天功能，可添加 `pod 'NEChatUIKit'` 和 `pod 'NEChatKit'`。

    **导入 UI 组件时，需要指定相同版本的基础 Kit 库引入，否则可能导致后续出现报错**。具体可参见下文的[常见问题排查](#pod-冲突报错)。

    :::note note
    IM UIKit 底层依赖 NIM SDK。
    - 若引入 UI 组件时不指定 NIM SDK 版本，那么将默认引入当前兼容的最新版本（参考[更新日志](https://doc.yunxin.163.com/messaging-uikit/guide/jE5MTA5NjA?platform=iOS)）。
    - 若引入 UI 组件时需要使用指定 NIM SDK 的版本，那么需要在引入时填写正确的版本号，具体请参考以下示例代码。
    :::

  :::::: div custom-tabs
  ::: tab 不指定 NIM SDK 版本
  ```swift
  # Uncomment the next line to define a global platform for your project
  platform :ios, '11.0'

  # 请使用您的真实项目名称替换 your project name
  target 'your project name' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!
  
  # 基础 Kit 库
  pod 'NEChatKit', '9.7.4'

  # UI 组件，依次为通讯录组件、会话列表组件、会话（聊天）组件、群相关设置组件
  pod 'NEContactUIKit', '9.7.4'
  pod 'NEConversationUIKit', '9.7.4'
  pod 'NEChatUIKit', '9.7.4'
  pod 'NETeamUIKit', '9.7.4'     

  # 扩展库-地理位置组件
  pod 'NEMapKit', '9.7.4'

  # 扩展库-呼叫组件
  pod 'NIMSDK_LITE','9.14.2'
  pod 'NERtcCallKit/NOS_Special', '2.2.0'
  pod 'NERtcCallUIKit/NOS_Special', '2.2.0'

  # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
  pod 'NERtcSDK/RtcBasic', '5.5.2'        
  pod 'NERtcSDK/Nenn'                    
  pod 'NERtcSDK/Segment'                  

  end
  ```
  :::
  ::: tab 指定 NIM SDK 版本
  ```swift
  # Uncomment the next line to define a global platform for your project
  platform :ios, '11.0'

  # 请使用您的真实项目名称替换 your project name
  target 'your project name' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # 指定 NIM SDK 版本，以9.11.0 为例
  pod 'NIMSDK_LITE','9.11.0'

  # 基础 Kit 库

  pod 'NECoreKit','9.6.5'
  pod 'NECommonKit','9.6.6'
  pod 'NECommonUIKit','9.7.1'
  pod 'NECoreIMKit/NOS_Special','9.6.7-rc40'
  pod 'NEChatKit/NOS_Special', '9.7.4'
  pod 'lottie-ios','2.5.3'

  # UI 组件，依次为通讯录组件、会话列表组件、会话（聊天）组件、群相关设置组件
  pod 'NEContactUIKit/NOS_Special', '9.7.4'      
  pod 'NEConversationUIKit/NOS_Special', '9.7.4' 
  pod 'NEChatUIKit/NOS_Special', '9.7.4'         
  pod 'NETeamUIKit/NOS_Special', '9.7.4'         

  # 扩展库-地理位置组件
  pod 'NEMapKit/NOS_Special', '9.7.4'         

  # 扩展库-呼叫组件
  pod 'NERtcCallKit/NOS_Special', '2.2.0'
  pod 'NERtcCallUIKit/NOS_Special', '2.2.0'

  # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
  pod 'NERtcSDK/RtcBasic', '5.5.2'         
  pod 'NERtcSDK/Nenn'                     
  pod 'NERtcSDK/Segment'                  

  end
  ```
  :::
  ::: tab （海外数据中心）不指定 NIM SDK 版本
  ```swift
  # Uncomment the next line to define a global platform for your project
  platform :ios, '11.0'

  # 请使用您的真实项目名称替换 your project name
  target 'your project name' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # 基础 Kit 库
  pod 'NEChatKit/FCS', '9.7.4'

  # UI 组件，依次为通讯录组件、会话列表组件、会话（聊天）组件、群相关设置组件
  pod 'NEContactUIKit/FCS', '9.7.4'      
  pod 'NEConversationUIKit/FCS', '9.7.4' 
  pod 'NEChatUIKit/FCS', '9.7.4'         
  pod 'NETeamUIKit/FCS', '9.7.4'         

  # 扩展库-地理位置组件
  pod 'NEMapKit/FCS', '9.7.4'         

  # 扩展库-呼叫组件
  pod 'NIMSDK_LITE/FCS','9.14.2'
  pod 'NERtcCallKit/FCS_Special', '2.2.0'
  pod 'NERtcCallUIKit/FCS_Special', '2.2.0'

  # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
  pod 'NERtcSDK/RtcBasic', '5.5.2'         
  pod 'NERtcSDK/Nenn'                     
  pod 'NERtcSDK/Segment'                  

  end
  ```
  :::
  ::: tab （海外数据中心）指定 NIM SDK 版本
  ```swift
  # Uncomment the next line to define a global platform for your project
  platform :ios, '11.0'

  # 请使用您的真实项目名称替换 your project name
  target 'your project name' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # 指定 NIM SDK 版本，以9.11.0 为例
  pod 'NIMSDK_LITE/FCS','9.11.0'

  # 基础 Kit 库
  pod 'NECoreKit','9.6.5'
  pod 'NECommonKit','9.6.6'
  pod 'NECommonUIKit','9.7.1'
  pod 'NECoreIMKit/NOS_Special','9.6.7-rc40'
  pod 'NEChatKit/FCS_Special', '9.7.4'
  pod 'lottie-ios','2.5.3'

  # UI 组件，依次为通讯录组件、会话列表组件、会话（聊天）组件、群相关设置组件
  pod 'NEContactUIKit/FCS_Special', '9.7.4'      
  pod 'NEConversationUIKit/FCS_Special', '9.7.4' 
  pod 'NEChatUIKit/FCS_Special', '9.7.4'         
  pod 'NETeamUIKit/FCS_Special', '9.7.4'         

  # 扩展库-地理位置组件
  pod 'NEMapKit/FCS_Special', '9.7.4'         

  # 扩展库-呼叫组件
  pod 'NERtcCallKit/FCS_Special', '2.2.0'
  pod 'NERtcCallUIKit/FCS_Special', '2.2.0'

  # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
  pod 'NERtcSDK/RtcBasic', '5.5.2'         
  pod 'NERtcSDK/Nenn'                     
  pod 'NERtcSDK/Segment'                  

  end
  ```
  :::
  ::::::

2. 配置完 “Podfile” 文件后执行`pod install`命令导入组件。

::: note note
- 各 UI 组件相互独立，添加或删除均不影响项目编译。
- 示例代码中的 9.6.3 为版本号，仅用于示例。建议使用最新版本。
    如果出现类似“版本不存在”的报错，可执行`pod update`命令，然后双击 `.xcworkspace` 文件，启动项目即可。
- 暂不支持 bitcode。
- 更多组件导入信息，请参见[组件导入](https://doc.yunxin.163.com/messaging-uikit/guide/TE1NzcyMzE?platform=iOS)。
:::


### 步骤2：初始化

1. 在项目中引入需要的组件。

    **示例代码：**

    :::::: div custom-tabs
    ::: tab Swift

    ``` 
    import NECoreKit
    import NECoreIMKit
    import NEChatKit
    import NEChatUIKit
    import NERtcCallUIKit
    ...
    ```
    :::
    ::: tab Objective-C
    ```
    #import <NECoreKit/NECoreKit-Swift.h>
    #import <NECoreIMKit/NECoreIMKit-Swift.h>
    #import <NEChatKit/NEChatKit-Swift.h>
    #import <NEChatUIKit/NEChatUIKit-Swift.h>
    #import <NERtcCallUIKit/NERtcCallUIKit.h>
    ...
    ```
    :::
    ::::::

2. 在应用启动后，调用 `setupCoreKitIM` 方法进行初始化。

    `option` 参数| 是否必传  |说明   
    ---  |----|----
    `appKey`   | 是 |   云信控制台获取到的 App Key    
    `apnsCername`   | 否  |    APNs 推送证书名，如不需要实现离线推送可不配置  
    `pkCername`    | 否   |   PushKit  推送证书名，如不需要实现离线推送可不配置


    **示例代码：**

    :::::: div custom-tabs
    ::: tab Swift

    ``` 
    let option = NIMSDKOption()
    option.appKey = "your app key"
    option.apnsCername = "云信控制台配置的 APNS 推送证书名称"
    option.pkCername = "云信控制台配置的 PushKit 推送证书名称"
    IMKitClient.instance.setupCoreKitIM(option)
    let _ = NEAtMessageManager.instance
    ```
    :::
    ::: tab Objective-C
    ```
    NIMSDKOption *option = [NIMSDKOption optionWithAppKey:AppKey];
    option.apnsCername = @"";
    option.pkCername = @"";
    [[IMKitClient instance] setupCoreKitIM:option];
    NEAtMessageManager * _ = [NEAtMessageManager instance];
    ```
    :::
    ::::::

::: note notice

更多初始化说明，请参见[初始化](https://doc.yunxin.163.com/messaging-uikit/guide/DQ1OTkyMjU?platform=iOS#初始化)。
:::

### 步骤3：登录

在完成初始化后，调用 `loginIM` 方法登录 IM。

**示例代码：**

:::::: div custom-tabs
::: tab Swift

```
    IMKitClient.instance.loginIM(accid, token) { error in
        if let err = error {
            print("NEKitCore login error : ", err)
        }else {
            //在登录成功回调中初始化路由以及配置各个模块首页
            /*
             weakSelf?.setupTabbar()
             */
        }
    }
```   
:::
::: tab Objective-C
```
[[IMKitClient instance] loginIM:@"accid" :@"token" :^(NSError * _Nullable error) {
    if (error != nil) {
        NSLog(@"NEKitCore login error : %@", [error description]);
    } else {
        //在登录成功回调中初始化路由以及配置各个模块首页
        /*
        [weakSelf setupTabbar];
        */
    }
}];
```
:::
::::::

::: note notice
调用登录的方法时，将示例代码中的 `accid` 和 `token` 分别替换为您的云信账号 ID （即 accid）和 Token。
:::

### 步骤4：初始化路由

如果未在登录成功回调中初始化路由，需要单独初始化路由，才能进行后续的界面搭建。在初始化路由时可同时初始化地图 Map，初始化后，您的应用即可实现地理位置消息功能。具体请参见[实现地理位置消息功能](https://doc.yunxin.163.com/messaging-uikit/guide/TE3MzA3ODk?platform=iOS)。

**示例代码：**

:::::: div custom-tabs
::: tab Swift
```
 func loadService() {
        //初始化路由
        ContactRouter.register()
        ChatRouter.register()
        TeamRouter.register()
        ConversationRouter.register()
        //注册个人设置页面，用于实现单击头像后跳转至个人设置页面功能
        Router.shared.register(MeSettingRouter) { param in
            if let nav = param["nav"] as? UINavigationController {
                let me = PersonInfoViewController()
                nav.pushViewController(me, animated: true)
            }
        }
        
        //地图map初始化
        NEMapClient.shared().setupMapClient(withAppkey: AppKey.gaodeMapAppkey)
    }
```
:::
::: tab Objective-C
```
- (void)registerRouter {
    [ContactRouter register];
    [ChatRouter register];
    [TeamRouter register];
    [ConversationRouter register];
        //注册个人设置页面，用于实现单击头像后跳转至个人设置页面功能
    [[Router shared] register:MeSettingRouter
                      closure:^(NSDictionary<NSString *, id> *_Nonnull param) {
        NSObject *param1 = [param objectForKey:@"nav"];
        if ([param1 isKindOfClass:[UINavigationController class]]) {
        UINavigationController *nav = (UINavigationController *)param1;
        PersonInfoViewController *me =
            [[PersonInfoViewController alloc] init];

        [nav pushViewController:me animated:YES];
        }
    }];

    //地图map初始化
    [[NEMapClient shared] setupMapClientWithAppkey:@"gaodeMap Appkey"];
}
```
:::
::::::


:::note notice
- 若需要注册个人设置页面，实现单击头像后跳转至个人设置页面的功能，首先需要在 XCode 中拖入相关的源码文件至您的工程。相关的源码文件包括：
    - app 下的 [Mine](https://github.com/netease-kit/nim-uikit-ios/tree/master/app) 文件
    - app 下 Assets 中的 [Mine](https://github.com/netease-kit/nim-uikit-ios/tree/master/app/Assets.xcassets) 文件

- 示例代码中的路由跳转都跳转至**基础版 UI 界面**，若需要使用**通用版 UI 界面**，切换注册路由方法即可。例如将 `ChatRouter.register()` 替换为 `ChatRouter.registerFun()`；`ContactRouter.register()` 替换为 `ContactRouter.registerFun()` 等。

:::


### 步骤5：界面搭建


:::::: div custom-tabs
::: tab 基础版 UI 界面搭建

以搭建单聊群聊页面为例，示例代码如下（更多详情请参见下文的[界面集成详情](#界面集成详情)）：

**示例代码：**

- Swift 示例：

    ```swift
    func chatExample(){
        let session = NIMSession("accid", type: .P2P)
        let p2pChatVC = P2PChatViewController(session: session)
            
        let teamSession = NIMSession("team id", type: .team)
        let groupVC = GroupChatViewController(session: teamSession, anchor: nil)
    }
    ```
- Objective-C 示例：

    ```
    - (void)chatExample {
        NIMSession *session = [NIMSession session:@"accid" type:NIMSessionTypeP2P];
        P2PChatViewController *p2pChatVC = [[P2PChatViewController alloc] initWithSession:session];
        
        NIMSession *teamSession = [NIMSession session:@"accid" type:NIMSessionTypeTeam];
        GroupChatViewController *groupVC = [[GroupChatViewController alloc] initWithSession:teamSession anchor:nil];
    }
    ```

**参数说明：**

参数 | 说明
---- | -------------- 
`accid` | 网易云信账号ID，可调用[注册云信 IM 账号](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQ3Nzk1MTY?platformId=60353) API 创建
`type` | 聊天类型，`.P2P`-单聊，`.team`-群聊

界面效果参考如下：

<img style="width:20%" src="https://yx-web-nosdn.netease.im/common/571cc360fc8d842637f0852924d7b257/消息已读未读蓝.png" />

:::
::: tab 通用版 UI 界面搭建

以搭建单聊群聊页面为例，示例代码如下：

**示例代码：**

- Swift 示例：

    ```swift
    func chatExample(){
        let session = NIMSession("accid", type: .P2P)
        let p2pChatVC = FunP2PChatViewController(session: session)
            
        let teamSession = NIMSession("team id", type: .team)
        let groupVC = FunGroupChatViewController(session: teamSession, anchor: nil)
    }
    ```

- Objective-C 示例：

    ```
    - (void)chatExample {
        NIMSession *session = [NIMSession session:@"accid" type:NIMSessionTypeP2P];
        FunP2PChatViewController *p2pChatVC = [[FunP2PChatViewController alloc] initWithSession:session];
        
        NIMSession *teamSession = [NIMSession session:@"accid" type:NIMSessionTypeTeam];
        FunGroupChatViewController *groupVC = [[FunGroupChatViewController alloc] initWithSession:teamSession anchor:nil];
    }
    ```

**参数说明：**

参数 | 说明
---- | -------------- 
`accid` | 网易云信账号ID，可调用[注册云信 IM 账号](https://doc.yunxin.163.com/docs/TM5MzM5Njk/DQ3Nzk1MTY?platformId=60353) API 创建
`type` | 聊天类型，`.P2P`-单聊，`.team`-群聊

界面效果参考如下：

<img style="width:20%" src="https://yx-web-nosdn.netease.im/common/7238398c864adbb2798bb279538aef47/消息已读未读.png" />

:::
::::::



## 后续步骤

为保障通信安全，如果您在调试环境中的使用的是云信控制台生成的测试用 IM 账号 和 token，请确保在后续的正式生产环境中，将其替换为通过 [IM 服务端 API](https://doc.yunxin.163.com/TM5MzM5Njk/docs/DQ3Nzk1MTY?platform=server) 生成的正式 IM 账号（accid）和 token。

## 相关参考

### 界面集成详情

IM UIKit 中提供的常用业务场景界面及相关集成说明如下：
页面 | 所属组件 | 描述
:---- | :-------------- | :---------
`ConversationController` | NEConversationUIKit | 会话列表页面（创建或者跳转到该界面需要传入参数，详见[集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/TkwMDY4MTM?platform=iOS)）<br/>修改界面 UI 请参见[自定义会话列表 UI](https://doc.yunxin.163.com/messaging-uikit/guide/TA3MzQ4Njc?platform=iOS)
`ContactsViewController` | NEContactUIKit | 通讯录页面（创建或者跳转到该界面需要传入参数，详见[集成通讯录界面](https://doc.yunxin.163.com/messaging-uikit/guide/DM5ODQ3NjY?platform=iOS)）<br/>修改界面 UI 请参见[自定义通讯录 UI](https://doc.yunxin.163.com/messaging-uikit/guide/zM4NTM3OTg?platform=iOS)
`P2PChatViewController`<br>`GroupChatViewController`  | NEChatUIKit | 单聊、群聊会话页面（创建或者跳转到该界面需要传入参数，详见[集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jgzMzgwNTY?platform=iOS)）<br/>修改界面 UI 请参见[自定义会话消息 UI](https://doc.yunxin.163.com/messaging-uikit/guide/DEzODYxOTI?platform=iOS)
`TeamSettingViewController` | NETeamKit | 群组设置页面

### 音视频通话

集成会话界面后，如果需要在会话消息界面实现音视频通话功能，请参见[实现音视频通话功能](https://doc.yunxin.163.com/messaging-uikit/guide/TA2MTk0Njg?platform=iOS)。


### 常见问题排查

#### pod 冲突报错

- **问题原因**


    如果执行[步骤1](#步骤1)导入组件时，只导入了 IM UIKit 的 UI 组件，在特殊情况下可能出现库版本不一致导致的报错（UI 组件版本与其内部依赖的基础 kit 库的版本不一致）。

    以下图所示的报错为例，导入的 IM UIKit 的 UI 组件版本为 v9.3.0，但导入的基础 Kit 库版本为 v9.3.2。这会导致基础库用到日志库（`alog`)和 UI 组件用到的 `alog` 不一致，进而导致 pod 冲突报错。


    ![POPO20230216-173017.png](https://yx-web-nosdn.netease.im/common/321c73405ca4a7b50a91ed24bb96f61e/POPO20230216-173017.png)


- **处理建议**：


    导入 UI 组件时，同时也指定推荐版本的基础 Kit 库。 

    以导入 v9.7.3 的 UI 组件为例：

    ```
    #基础kit库
    pod 'NECommonUIKit', '9.7.1'
    pod 'NECommonKit', '9.6.6'
    pod 'NECoreIMKit', '9.6.7'
    pod 'NECoreKit', '9.6.6'
    ```

#### 集成报错处理

当集成时出现以下报错信息：

![集成报错.png](https://yx-web-nosdn.netease.im/common/e2a1bde8daf6c6bab6d600f739d16e35/集成报错.png)

原因是无法确定 Swift 的具体版本，请在 Podfile 中添加 `ENV['SWIFT_VERSION'] = '5'`，指定 Swift 版本。


