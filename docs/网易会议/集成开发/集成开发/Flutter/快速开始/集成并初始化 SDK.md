本文主要介绍如何集成 NEMeetingKit，并对会议组件进行初始化。

## 开发环境

在客户端实现音视频会议功能之前，请您准备以下开发环境：

| 环境类型 | 具体要求 |
| ---- | ---- |
| Flutter 版本 | 3.29.3 |
| JDK 版本 | 17 及以上版本 |
| IDE | Android Studio |\
| | <br> Android Studio需要安装Flutter&Dart插件，支持Flutter框架编译运行。 |

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案或者开通 **PaaS 会议组件服务**。具体步骤可参考 [开通方案](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 集成 SDK

1. 新建 Flutter 工程。若已存在工程，请跳过该步骤。

    配置 Flutter 环境后，可运行如下命令创建新的应用工程。

    ```
    flutter create --platforms android,ios
    ```

2. 添加 SDK 编译依赖。

    修改项目的 `pubspec.yaml` 文件，添加会议组件依赖，最新版本号请参见更新日志。

    ```
    netease_meeting_kit: ^x.x.x
    ```

## 初始化

### 调用时机

在调用 SDK 其他接口之前，您首先需要完成初始化操作。

### 注意事项

- 初始化是一个异步操作，您需要确保异步回调成功之后，再进行调用 API。
- 应用名称会显示在会议界面的顶部标题栏中。若不额外设置应用名称，则标题默认显示为 **会议**。
<!--默认情况下，这里不需要手动配置，sdk 会自动检测并配置
- 请在初始化网易会议组件 SDK 时配置前台服务，防止会议进程退到后台时被系统杀死，且保证使用 Android 系统可以正常共享屏幕。详细配置参考 `NEForegroundServiceConfig`类。
-->

### 调用步骤

1. 配置初始化相关参数，详情请参考 `NEMeetingKitConfig` 类。

   **示例代码如下：**

    ```Dart
    final foregroundServiceConfig = NEForegroundServiceConfig(
      contentTitle: '网易会议',
      contentText: '网易会议正在运行中',
      ticker: '网易会议',
      channelId: 'netease_meeting_channel',
      channelName: '网易会议',
      channelDesc: '网易会议',
    );
    final config = NEMeetingKitConfig(
        // 前提条件中，获取的会议AppKey
        appKey: appKey,
        // 企业码,可选
        corpCode: corpCode,
        appName: '网易会议',
        // 设置iOS屏幕共享的AppGroup
        iosBroadcastAppGroup: 'group.com.netease.yunxin.meeting',
        iosBroadcastScheme: 'nemeeting://',
        foregroundServiceConfig: foregroundServiceConfig,
      );
    ```
    
2. 调用 `initialize` 方法完成初始化操作。

   **示例代码如下：**

    ```Dart
    NEMeetingKit.instance.initialize(config).then((value) {
      if (value.isSuccess()) {
        // 初始化成功
      } else {
        // 初始化失败，打印错误信息
      }
    });
    ```
3. （可选）当您不确定是否已经初始化会议组件，可调用 `isInitialized` 添加查询是否已经初始化的调用。

   **示例代码如下：**

    ```Dart
    // 检查会议组件是否已经初始化
    final isInitialized = NEMeetingKit.instance.isInitialized;
    if (isInitialized) {
        // 如果已经初始化，执行后续操作
        // ...
    } else {
        // 如果未初始化，可能需要重新初始化或者记录日志
    }
    ```