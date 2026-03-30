

网易云信在 GitHub 上提供开源的圈组 Demo 源码。您可参考 Demo 源码，在您的本地项目中快速构建即时通讯应用。

本文介绍如何快速跑通圈组 Demo 源码。

:::note notice
圈组 Demo (iOS) 源码仅支持在真机上运行。
:::


## 前提条件


在开始运行示例项目之前，请确保您已：

- 已通过[功能概览]()了解圈组相关基础概念和功能。
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/zQ3ODUyNjk?platform=iOS#4-注册-im-账号)，获取 accid 和 token。
- 开发环境满足以下要求:

    - Xcode 12 及以上版本
    - iOS 10.0 及以上版本

如果您需要使用搭载 Apple M1 处理器芯片的设备（如 MacBook）运行圈组 Demo 源码，请务必在设备的操作系统中完成如下配置：
1. 进入**访达->应用程序**。
2. 右键单击 **Xcode**，并选择**显示简介**。
3. 勾选 **使用 Rosetta 打开**。


    ![AppleM1.png](https://yx-web-nosdn.netease.im/common/9ff06382d074151cd02b56d6d58def67/AppleM1.png)


## 跑通流程


1. 前往 GitHub <a href="https://github.com/netease-kit/qchat-uikit-ios" target="_blank">下载圈组 Demo 源码</a>。

2. 进入到 Podfile 所在目录（即根目录），执行 ```pod install```。

    若报错，请执行 ```pod update```。

3. 双击 **IMQChatExample.xcworkspace**，打开项目。

4. 在工程目录的 ```IMQChatExample/Main/AppKey.swift``` 文件中，将如下代码中的 ```<#请输入appkey#>```替换成您的 App Key, 将如下代码中的 ```<#accid#>```和```<#token#>```分别替换成您的云信账号 ID（accid）和 token。
    ```
    public let account = "<#accid#>"
    public let token = "<#token#>"

      public static let appKey = "<#请输入appkey#>"
   
    ```

5. 将示例项目运行在您的真机设备上，即可开始体验圈组相关功能。
