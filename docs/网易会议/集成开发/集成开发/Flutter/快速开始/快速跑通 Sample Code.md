本文主要介绍如何快速跑通网易会议组件的 [Flutter Sample Code](https://github.com/GrowthEase/NetEase_Meeting/tree/main/meeting-flutter)，体验在线的多人视频会议功能。

该示例项目包含了详细的 API 调用场景、参数封装以及回调处理。包含的功能如下：

- 通过账号、密码完成会议组件的登录鉴权、注销登录。
- 预约会议、创建会议、加入会议。
- 会议内提供的其他功能（如会议控制、屏幕共享等）。

<!--
## Sample Code 说明

功能| 网易会议 AppKey | 网易会议账号
--- | --- | ---
加入会议 | 需要 | 不需要
创建会议 | 需要 | 需要
预约会议 | 需要 | 需要
-->

## 开发环境

在开始运行示例项目之前，请您准备以下开发环境：

| 环境类型 | 具体要求 |
| ---- | ---- |
| Flutter 版本 | 3.29.3 |
| JDK 版本 | 17 及以上版本 |
| IDE | Android Studio |\
| | <br> Android Studio 需要安装 Flutter&Dart 插件，支持 Flutter 框架编译运行。 |

## 前提条件

- 在网易云信控制台创建至少一个应用，获取应用的 AppKey。若无应用，请参考 [创建应用并获取 AppKey](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA)。

- 开通 **视频会议** 解决方案或者开通 **PaaS 会议组件服务**，具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 下载 Sample Code

1. 从 github 下载网易会议组件 Flutter Sample Code 源码，或者直接在命令行运行以下命令：

    ```
    git clone https://github.com/GrowthEase/NetEase_Meeting.git
    ```

2. 通过 Android Studio 打开 `NetEase_Meeting/meeting-flutter` 项目。

## 配置 Sample Code

打开工程，在工程的对应文件中填写您的会议组件 AppKey。 

- Android: `NetEase_Meeting/meeting-flutter/meeting_app/android/app/src/main/assets/xkit_server.config` 
- iOS: `NetEase_Meeting/meeting-flutter/meeting_app/ios/Runner/xkit_server.config` 

```XML
{
  "appkey": "{这里替换成你的AppKey}"
  ...
}
```

## 运行 Sample Code

您在申请并声明 AppKey 后，下面开始运行并编译示例项目，

首次运行需要找到 `meeting_app/lib/main.dart` 应用程序的入口文件，点击 `main()` 旁的运行按钮，后续 IDE 会记忆应用运行入口。

::: note note
若未找到 `main()` 函数旁的运行按钮，可能是 IDE Flutter 环境配置问题，没有识别为 Flutter 可运行程序，可以检查相关 Flutter 配置后重试。
:::

编译并运行后即可体验 **登录**、**预约会议**、**加入会议**、**创建会议** 功能。

效果图如下所示：

<img style="width:30%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/6d0b24b86c99a15dd21139059e9dfe65/meeting_entry_20260104.jpg" alt="meetingkit_demo_main" />