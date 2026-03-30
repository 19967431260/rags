网易云信在提供开源的 IM Demo 源码。您可参考 Demo 源码，在您的 Flutter 项目中快速构建即时通讯应用。本文介绍如何快速跑通 IM Demo 源码。

## 界面模块

IM Demo（Flutter）主要包含会话列表，会话和通讯录三大界面模块，支持的功能包括单聊消息收发、群聊消息收发、会话管理、群组管理等。

<img style="width:70%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/4edebe6ecffee04e61fcc25ad8f80267/FlutterUIKit主要模块.png"/>

## 源码

Flutter（Android & iOS） | Flutter（Android & iOS & HarmonyOS）
:---: | :---: |
`nim-uikit-flutter`<br>[GitHub 源码](https://github.com/netease-kit/nim-uikit-flutter) 或 [Gitee 源码](https://gitee.com/netease-yunxin/nim-uikit-flutter) | `nim-uikit-flutter-ohos`<br>[GitHub 源码](https://github.com/netease-kit/nim-uikit-flutter-ohos) 或 [Gitee 源码](https://gitee.com/netease-yunxin/nim-uikit-flutter-ohos)

## 准备工作

在开始运行示例项目之前，请确保您已完成以下操作：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key。
2. [注册 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/TUwNTQ2NjM?platform=flutter#4-注册-im-账号)，获取账号 ID（`accid`）和 token。
3. 准备如下开发环境和工具：

    - Dart 3.5 及以上版本。
    - 开发环境：

    :::::: div linked-codes
    ::: code Android
    - Android Studio Bumblebee
    - App 要求 Android API 24 及以上版本设备
    - 1.6.10 以上版本的 `kotlin-gradle-plugin`
    :::
    ::: code iOS
    - Xcode 12.0 及以上版本
    - App 要求 iOS 12.0 以上版本设备
    - 项目已设置有效的开发者签名
    :::
    ::: code HarmonyOS
    - DevEco Studio 5.1.1
    - Flutter 版本：3.27.5-ohos-0.0.2
    :::
    ::::::

## 运行源码

1. 下载 [IM Demo 源码](#源码)。

    示例项目结构如下：

    目录 | 说明
    ---- | ----
    `im_demo` | 应用主入口，包含外部界面框架
    `nim_chatkit_ui` | 聊天功能界面相关代码
    `nim_contactkit_ui` | 通讯录功能界面相关代码
    `nim_conversationkit_ui` | 会话功能界面相关代码
    `nim_searchkit_ui` | 搜索功能界面相关代码
    `nim_teamkit_ui` | 群组功能界面相关代码

2. 将示例项目导入您的开发工具。安卓项目推荐使用 Android Studio。

3. 在项目中，找到 `im_demo/lib/src/config.dart` 文件，将文件里如下代码中的 `your app key` 替换成您在前文准备工作阶段获取的 App Key。

    ```Dart
    class IMDemoConfig {
      static const AppKey = 'your app key';
    }
    ```

4. 在项目中找到 `im_demo/lib/src/home/splash_page.dart` 文件，将文件里找到 `startLogin` 方法设置成您在前文准备工作阶段获取的 IM 账号和 Token。

    ```Dart
    void startLogin() {
      //将您的 IM 账号(accid) 和 Token 设置在这里即可
      String account = "";
      String token = "";
      ......
    }
    ```

5. 运行源码到您的设备上，即可进入 Demo 界面，开始体验 IM Demo。