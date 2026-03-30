<!--keywords: UIKit,QChat,UI,UI组件库,UI界面,集成,SDK集成,新手 -->

网易云信圈组 UIKit（QChat UIKit）是基于 NetEase Instant Messaging SDK（以下简称 NIM SDK）中的圈组模块开发的一款[圈组 UI 组件库](https://doc.yunxin.163.com/messaging-uikit/guide/TA0MjAyNjU?platform=iOS)。本文介绍如何集成圈组 UIKit 到您的即时通讯项目中。


## 前提条件

在开始集成圈组 UIKit 前，请确保：
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/zQ3ODUyNjk?platform=iOS#4-注册-im-账号)，获取 accid 和 token。
- 已[获取示例项目](https://github.com/netease-kit/QChat-uikit-ios)。
- 已准备如下开发环境/工具：
    - iOS 13.0 及以上版本
    - Xcode 11.0 及以上版本

## 实现流程

@startuml
!include https://raw.githubusercontent.com/bschwarz/puml-themes/master/themes/cerulean-outline/puml-theme-cerulean-outline.puml
(*) -right-> "按需导入组件"
-right-> "初始化"
-right-> "登录"
-right-> "页面搭建"
-right-> (*)
@enduml

### <span id="步骤1">步骤1：按需导入组件</div>

1. 根据业务需要，在 “Podfile” 文件中，以添加依赖的形式添加相应的圈组 UIKit 组件。同时，你也可以引入 IM UIKit 的组件库（比如需要通讯录功能和会话列表功能，可添加 NEContactUIKit 和 NEConversationUIKit）各组件相互独立，添加或删除均不影响项目编译。

    **导入 UI 组件时，需要指定相同版本的基础 Kit 库引入，否则可能导致后续出现报错**。具体可参见下文的[常见问题排查](#pod-冲突报错)。

    :::::: div custom-tabs
    ::: tab 不指定 NIM SDK 版本
    ```swift
    # Uncomment the next line to define a global platform for your project
    platform :ios, '13.0'

    # 请使用您的真实项目名称替换 your project name
    target 'your project name' do
    # Comment the next line if you don't want to use dynamic frameworks
    use_frameworks!

    # 圈组组件
    pod 'NEQChatUIKit', '10.0.1' 
    # 通讯录组件（可选）       
    pod 'NEContactUIKit', '10.8.6'   
    # 会话列表组件（可选）    
    pod 'NEConversationUIKit', '10.8.6'  
    # 会话（聊天）组件（可选）
    pod 'NEChatUIKit', '10.8.6'  
    # 群相关设置组件（可选）        
    pod 'NETeamUIKit', '10.8.6'          

    # 基础 Kit 库
    pod 'NEChatKit', '10.8.6'
    pod 'NEQChatKit', '10.0.1'

    # 扩展库-地理位置组件
    pod 'NEMapKit', '10.8.6'         

    # 扩展库-呼叫组件
    pod 'NERtcCallKit/NOS_Special', '3.6.0'
    pod 'NERtcCallUIKit/NOS_Special', '3.6.0'
    
    # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
    pod 'NERtcSDK/RtcBasic'     
    pod 'NERtcSDK/Nenn'                    
    pod 'NERtcSDK/Segment'   
    end
    ```
    :::
    ::: tab 指定 NIM SDK 版本
    ```swift
    # Uncomment the next line to define a global platform for your project
    platform :ios, '13.0'
    
    # 请使用您的真实项目名称替换 your project name
    target 'your project name' do
    # Comment the next line if you don't want to use dynamic frameworks
    use_frameworks!

    # 指定 NIM SDK 版本，以 10.8.20 为例
    pod 'NIMSDK_LITE','10.8.20'
    pod 'NIMSDK_LITE/QChat','10.8.20'

    # 圈组组件 
    pod 'NEQChatUIKit/NOS_Special', '10.0.1' 
    # 通讯录组件（可选）       
    pod 'NEContactUIKit/NOS_Special', '10.8.6'   
    # 会话列表组件（可选）    
    pod 'NEConversationUIKit/NOS_Special', '10.8.6'  
    # 会话（聊天）组件（可选） 
    pod 'NEChatUIKit/NOS_Special', '10.8.6'  
    # 群相关设置组件（可选）        
    pod 'NETeamUIKit/NOS_Special', '10.8.6'          

    # 基础 Kit 库
    pod 'NECoreKit','9.8.0'
    pod 'NECommonKit','9.7.4'
    pod 'NECommonUIKit','9.8.1'
    pod 'NECoreIM2Kit/NOS_Special','1.1.5'
    pod 'NEChatKit/NOS_Special', '10.8.6'
    pod 'NEQChatKit/NOS_Special', '10.0.1'  
    pod 'lottie-ios', '2.5.3'
    
    # 扩展库-地理位置组件
    pod 'NEMapKit/NOS_Special', '10.8.6'         

    # 扩展库-呼叫组件
    pod 'NERtcCallKit/NOS_Special', '3.6.0'
    pod 'NERtcCallUIKit/NOS_Special', '3.6.0'

    # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
    pod 'NERtcSDK/RtcBasic'       
    pod 'NERtcSDK/Nenn'                    
    pod 'NERtcSDK/Segment'   
    end
    ```
    :::
    ::: tab （海外数据中心）不指定 NIM SDK 版本
    ```swift
    # Uncomment the next line to define a global platform for your project
    platform :ios, '13.0'

    # 请使用您的真实项目名称替换 your project name
    target 'your project name' do
    # Comment the next line if you don't want to use dynamic frameworks
    use_frameworks!

    # 圈组组件
    pod 'NEQChatUIKit/FCS', '10.0.1' 
    # 通讯录组件（可选）       
    pod 'NEContactUIKit/FCS', '10.8.6'   
    # 会话列表组件（可选）    
    pod 'NEConversationUIKit/FCS', '10.8.6'  
    # 会话（聊天）组件（可选）
    pod 'NEChatUIKit/FCS', '10.8.6'  
    # 群相关设置组件（可选）        
    pod 'NETeamUIKit/FCS', '10.8.6'          

    # 基础 Kit 库
    pod 'NEChatKit/FCS', '10.8.6'
    pod 'NEQChatKit/FCS', '10.0.1'

    # 扩展库-地理位置组件
    pod 'NEMapKit/FCS', '10.8.6'         

    # 扩展库-呼叫组件
    pod 'NERtcCallKit/FCS_Special', '3.6.0'
    pod 'NERtcCallUIKit/FCS_Special', '3.6.0'

    # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
    pod 'NERtcSDK/RtcBasic'       
    pod 'NERtcSDK/Nenn'                    
    pod 'NERtcSDK/Segment'   
    end
    ```
    :::
    ::: tab （海外数据中心）指定 NIM SDK 版本
    ```swift
    # Uncomment the next line to define a global platform for your project
    platform :ios, '13.0'

    # 请使用您的真实项目名称替换 your project name
    target 'your project name' do
    # Comment the next line if you don't want to use dynamic frameworks
    use_frameworks!

    # 指定 NIM SDK 版本，以 10.8.20 为例
    pod 'NIMSDK_LITE/FCS','10.8.20'
    pod 'NIMSDK_LITE/QChat','10.8.20'

    # 圈组组件
    pod 'NEQChatUIKit/FCS_Special', '10.0.1' 
    # 通讯录组件（可选）       
    pod 'NEContactUIKit/FCS_Special', '10.8.6'   
    # 会话列表组件（可选）    
    pod 'NEConversationUIKit/FCS_Special', '10.8.6'  
    # 会话（聊天）组件（可选）
    pod 'NEChatUIKit/FCS_Special', '10.8.6'  
    # 群相关设置组件（可选）        
    pod 'NETeamUIKit/FCS_Special', '10.8.6'          

    # 基础 Kit 库
    pod 'NECoreKit','9.8.0'
    pod 'NECommonKit','9.7.4'
    pod 'NECommonUIKit','9.8.1'
    pod 'NECoreIM2Kit/FCS_Special','1.1.5'
    pod 'NEChatKit/FCS_Special', '10.8.6'
    pod 'NEQChatKit/FCS_Special', '10.0.1'  
    pod 'lottie-ios', '2.5.3'

    # 扩展库-地理位置组件
    pod 'NEMapKit/FCS_Special', '10.8.6'         

    # 扩展库-呼叫组件
    pod 'NERtcCallKit/FCS_Special', '3.6.0'
    pod 'NERtcCallUIKit/FCS_Special', '3.6.0'

    # 扩展库，依次为 RTC 音视频基础组件、RTC 音视频神经网络组件（使用背景虚化功能需要集成）、RTC 音视频背景分割组件（使用背景虚化功能需要集成）
    pod 'NERtcSDK/RtcBasic'       
    pod 'NERtcSDK/Nenn'                    
    pod 'NERtcSDK/Segment'   
    end
    ```
    :::
    ::::::

    ::: note notice
    - 各 UI 组件相互独立，添加或删除均不影响项目编译。
    - 示例代码中的 10.0.1 为版本号，仅用于示例。建议使用最新版本。
    - 暂不支持 bitcode。
    :::


2. 配置完 “Podfile” 文件后执行`pod install`命令导入组件。



### 步骤2：初始化


1. 在项目中引入需要的组件。

    **示例代码：**

    :::::: div custom-tabs
    ::: tab Swift

    ``` 
    import NECoreKit
    import NECoreIM2Kit
    import NEQChatUIKit
    import NERtcCallUIKit
    ...
    ```
    :::
    ::: tab Objective-C
    ```
    #import <NECoreKit/NECoreKit-Swift.h>
    #import <NECoreIM2Kit/NECoreIM2Kit-Swift.h>
    #import <NEQChatKit/NEQChatKit-Swift.h>
    #import <NEQChatUIKit/NEQChatUIKit-Swift.h>
    #import <NERtcCallUIKit/NERtcCallUIKit.h>
    ...
    ```
    :::
    ::::::

2. 在应用启动后，调用 `setupIM2` 方法进行初始化。

    `NIMSDKOption` 参数说明如下：

    `NIMSDKOption` 参数 | 是否必传 | 说明
    --- | ---- | ----
    `appKey` | 是 | 网易云信控制台获取到的 App Key。
    `apnsCername` | 否 | APNs 推送证书名，如不需要实现离线推送可不配置。
    `pkCername` | 否 | PushKit 推送证书名，如不需要实现离线推送可不配置。
    `avoidNosAccelerationBuckets` | 否 | 不走 NOS 域名加速的桶名集合。
    `v2` | 否 | 启用 V2 版本的 API。<note type=notice>该字段自 V10.6.1 版本起废弃。若仍需要使用 V1 的登录接口，请设置 `V2NIMSDKOption.useV1Login` 字段

    `V2NIMSDKOption` 参数说明如下：

    `V2NIMSDKOption` 参数 | 是否必传 | 说明
    --- | ---- | ----
    `useV1Login` |否 | 是否使用旧的登录接口，默认 NO，不使用
    `enableV2CloudConversation` | 否 | 是否使用 V2 云端会话，默认 NO，不使用

    ::: note notice
    SDK 默认使用本地会话，若需要使用云端会话功能，除了在组件导入时，引入云端会话外，还需要在初始化时，将 `enableV2CloudConversation` 设置为 YES。只有设置为 YES 后，才能正常使用云端会话服务。
    :::

    **示例代码**：

    :::::: div custom-tabs
    ::: tab Swift
    ```Swift
    // init
    // 设置IM SDK的配置项，包括AppKey，推送配置和一些全局配置等
    let option = NIMSDKOption()
    option.appKey = "your app key"
    option.apnsCername = "网易云信控制台配置的 APNS 推送证书名称"
    option.pkCername = "网易云信控制台配置的 PushKit 推送证书名称"

    // 设置IM SDK V2的配置项，包括是否使用旧的登录接口和是否使用云端会话
    let v2Option = V2NIMSDKOption()
    v2Option.enableV2CloudConversation = false

    // 初始化IM UIKit，初始化Kit层和IM SDK，将配置信息透传给IM SDK。无需再次初始化IM SDK
    IMKitClient.instance.setupIM2(option, v2Option)
    ```
    :::
    ::: tab Objective-C
    ```Objective-C
    // 设置IM SDK的配置项，包括AppKey，推送配置和一些全局配置等
    NIMSDKOption *option = [NIMSDKOption optionWithAppKey:AppKey];

    // 设置IM SDK V2的配置项，包括是否使用旧的登录接口和是否使用云端会话
    V2NIMSDKOption *v2Option = [[V2NIMSDKOption alloc] init];
    v2Option.enableV2CloudConversation = NO;

    // 初始化IM UIKit，初始化Kit层和IM SDK，将配置信息透传给IM SDK。无需再次初始化IM SDK
    [IMKitClient.instance setupIM2:option :v2Option];
    ```
    :::
    ::::::

::: note notice

更多初始化说明，请参考 [初始化](https://doc.yunxin.163.com/messaging-uikit/guide/TA4Nzk0NTE?platform=iOS#初始化)。
:::

### 步骤 3：登录

在完成初始化后，调用 `login` 方法登录 IM。

**示例代码**：

:::::: div custom-tabs
::: tab Swift

```Swift
    IMKitClient.instance.login(account, token, nil) { error in
        if let err = error {
            print("IMKitClient login error : ", err)
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
```Objective-C
[[IMKitClient instance] login:@"account" :@"token" :nil :^(NSError * _Nullable error) {
    if (error != nil) {
        NSLog(@"IMKitClient login error : %@", [error description]);
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
调用登录的方法时，将示例代码中的 `account` 和 `token` 分别替换为您的网易云信账号 ID 和 Token。
:::

### 步骤4：界面搭建

以搭建圈组 home 页面为例，更多页面请参见[界面集成详情](#界面集成详情)。

**示例代码：**

:::::: div custom-tabs
::: tab Swift
```swift
func qChatExample(){
    let qChatVC = QChatHomeViewController()
    qChatVC.delegate = self
}
```
:::
::: tab Objective-C
```
- (void)qChatExample {
    QChatHomeViewController *qChatVC = [[QChatHomeViewController alloc] init];
    qChatVC.delegate = self;
}
```
:::
::::::
  

界面效果参考如下：

<img style="width:20%" src="https://yx-web-nosdn.netease.im/common/4726f73906158cbe04baa91bed98cc87/社区列表.png" />


## 后续步骤

为保障通信安全，如果您在调试环境中的使用的是云信控制台生成的测试用 IM 账号 和 token，请确保在后续的正式生产环境中，将其替换为通过 [IM 服务端 API](https://doc.yunxin.163.com/TM5MzM5Njk/docs/DQ3Nzk1MTY?platform=server) 生成的正式 IM 账号（accid）和 token。

## 相关参考

### 界面集成详情

圈组 UIKit 中提供的常用业务场景界面及相关集成说明如下：
页面 | 所属组件 | 描述
:---- | :-------------- | :---------
`QChatSquareHomeViewController` | NEQChatUIKit | 圈组广场页面，展示内容包括不同类型下的广场频道等。
`QChatHomeViewController` | NEQChatUIKit | 圈组 home 页面，展示内容包括加入的社区，每个社区中的话题等。
`QChatViewController`  | NEQChatUIKit | 圈组会话页面（创建或者跳转到该界面需要传入参数）
`QChatServerSettingViewController` | NEQChatUIKit | 社区 设置页面（创建或者跳转到该界面需要设置社区参数）
`QChatChannelSettingVC` | NEQChatUIKit | 话题设置页面（创建或者跳转到该界面需要设置话题参数）


### 常见问题排查

#### pod 冲突报错

- **问题原因**


    如果执行[步骤1](#步骤1)导入组件时，只导入了圈组 UIKit 的 UI 组件，在特殊情况下可能出现库版本不一致导致的报错（UI 组件版本与其内部依赖的基础 kit 库的版本不一致）。

    例如导入的圈组 UIKit 的 UI 组件版本为 v9.5.3，但导入的基础 Kit 库版本为 v9.3.2。这会导致基础库用到日志库（`alog`)和 UI 组件用到的 `alog` 不一致，进而导致 pod 冲突报错。


- **处理建议**：


    导入 UI 组件时，同时也指定推荐版本的基础 Kit 库。 

    以导入 v9.5.3 的 QChat UI 组件为例，推荐的基础 Kit 库版本为：

    ```
    #基础kit库
    pod 'NECommonUIKit', '9.6.5'
    pod 'NECommonKit', '9.6.4'
    pod 'NECoreQChatKit', '9.6.5'
    pod 'NECoreKit', '9.6.3'
    ```



