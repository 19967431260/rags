网易云信在 Github 上提供开源的 IM Demo 源码。您可参考 Demo 源码，在您的本地项目中快速构建即时通讯应用。

本文介绍如何快速跑通 IM Demo 源码。

## Demo 主要模块

:::::: div custom-tabs
::: tab 基础版 UI
<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/11707474727796454a82bfdf823f5534/960主要模块.png" />
:::
::: tab 通用版 UI
<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/1d225879d3f6eda6e3a8027462f3dc60/960主要模块绿.png" />
:::
::::::


## 前提条件
在开始运行示例项目之前，请确保：

- 已在云信控制台 [创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key。
- 已 [注册云信 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取 accid 和 token。
- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 为应用开通 **云端会话** 开关。开启步骤请参考《控制台文档》[配置应用](https://doc.yunxin.163.com/console/concept/TQ2NzE5MzQ?platform=console)。

    ![开通云端会话.png](https://yx-web-nosdn.netease.im/common/d80e78c7f8d0a5b7f0452e7f5d9c6b47/开通云端会话.png)
- 开发环境满足以下要求:
  环境要求         | 说明                                                         
  ---------------- | -------------------
  Xcode 版本         | Xcode 12 及以上版本                                             
  iOS 系统版本        | iOS 10.0+   

如果您需要使用搭载 Apple M1 处理器芯片的设备（如 MacBook）运行 Demo 源码，请务必在设备的操作系统中完成如下配置：
1. 进入**访达->应用程序**。
2. 右键单击 **Xcode**，并选择**显示简介**。
3. 勾选 **使用 Rosetta 打开**。


    ![AppleM1.png](https://yx-web-nosdn.netease.im/common/9ff06382d074151cd02b56d6d58def67/AppleM1.png)


## 运行示例项目源码


:::::: div custom-tabs
::: tab Swift

1. 前往 GitHub [下载 IM Demo 源码](https://github.com/netease-kit/nim-uikit-ios)。

    Demo 目结构如下： 
     目录   | 说明  
     ----  | ----  
     app  | 应用主入口，包含外部界面框架 
     NEChatUIKit | 聊天功能界面相关代码
     NEContactUIKit | 通讯录功能界面相关代码
     NEConversationUIKit | 会话功能界面相关代码
     NETeamUIKit | 群组功能界面相关代码
     NEMapKit | 地图组件相关代码
     NERtcCallUIKit | 音视频呼叫界面相关代码



2. 进入到 swift 示例工程的 Podfile 所在目录（即根目录），执行 ```pod install```。中间如果报错，请执行 `pod update`。

3. 双击 **app.xcworkspace**，打开项目。

4. 找到工程目录里的 `app/Main/AppKey.swift` 文件。

    - 将如下代码中的 `<#请输入appkey#>` 替换成您的 [App Key](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)。

        ```
        public static let appKey = "<#请输入appkey#>"
        ```
    
    - 将如下代码中的 `<#account#>` 和 `<#token#>` 分别替换成您的云信 IM 账号（account）和 Token。如何获取，请参考 [注册 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/zQ3ODUyNjk?platform=iOS#4-注册-im-账号)。
    
        ```   
        public let account = "<#account#>"
        public let token = "<#token#>"
        ```
    
5. 将源码运行在您的真机设备上，即可进入如下界面，开始体验 IM Demo。

    可以在**我的->设置->外观**中切换 UI 风格。

    <table><thead><tr>
    <th style="width:50%">Demo 界面</th><th>UI 切换</th></tr></thead>
    <body>           
    <tr>
      <td><img src="https://yx-web-nosdn.netease.im/common/6858362055e77fc8a23285b63b0965be/Demo首页不含圈组.png" /></td>
      <td><img src="https://yx-web-nosdn.netease.im/common/1155b31d27fee93ced7a4bb146c8a6e8/UI切换图.png" /></td>
    </tr>
    </body>
    </table>

:::
::: tab Objective-C

1. 前往 GitHub [下载 IM Demo 源码](https://github.com/netease-kit/nim-uikit-ios)。

    Demo 目结构如下： 
     目录   | 说明  
     ----  | ----  
     IMUIKitOC  | OC 示例工程入口
     NEChatUIKit | 聊天功能界面相关代码
     NEContactUIKit | 通讯录功能界面相关代码
     NEConversationUIKit | 会话功能界面相关代码
     NETeamUIKit | 群组功能界面相关代码
     NEMapKit | 地图组件相关代码
     NERtcCallUIKit | 音视频呼叫界面相关代码

2. 进入到 OC 示例工程的 Podfile 所在目录（`IMUIKitOC/IMUIKitOCExample/`），执行 `pod install`。中间如果报错，请执行 `pod update`。
3. 双击 **IMUIKitOCExample.xcworkspace**，打开项目。
4. 找到 OC 工程目录里的 `IMUIKitOCExample/AppKey.h` 文件，将如下代码中的 `your appKey` 替换成您的 [App Key](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)。
    ```
    static NSString *const AppKey = @"your appKey";
    ```
5. 找到 OC 工程目录里的 `IMUIKitOCExample/Main/AppDelegate.m` 文件，将如下代码中的 `imaccid` 和 `imToken` 分别替换成您的云信 IM 账号（accid）和 Token。如何获取，请参考[注册 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/zQ3ODUyNjk?platform=iOS#4-注册-im-账号)。
    ```
    - (void)setupInit {
    // 初始化NIMSDK
    NIMSDKOption *option = [NIMSDKOption optionWithAppKey:AppKey];
    [[IMKitClient instance] setupCoreKitIM:option];
        
        // 登录IM之前先初始化 @ 消息监听mananger
        NEAtMessageManager * _ = [NEAtMessageManager instance];
        
        [[IMKitClient instance] loginIM:@"imaccid" :@"imToken" :^(NSError * _Nullable error) {
            if (error != nil) {
                NSLog(@"NEKitCore login error : %@", [error description]);
            } else {
                [self setupTabbar];
            }
        }];
    }
    ```
6. 将源码运行在您的真机设备上，即可进入如下界面，开始体验 IM Demo。

    可以在**我的->设置->外观**中切换 UI 风格。

    <table><thead><tr>
    <th style="width:50%">Demo 界面</th><th>UI 切换</th></tr></thead>
    <body>           
    <tr>
      <td><img src="https://yx-web-nosdn.netease.im/common/6858362055e77fc8a23285b63b0965be/Demo首页不含圈组.png" /></td>
      <td><img src="https://yx-web-nosdn.netease.im/common/1155b31d27fee93ced7a4bb146c8a6e8/UI切换图.png" /></td>
    </tr>
    </body>
    </table>
:::
::::::

