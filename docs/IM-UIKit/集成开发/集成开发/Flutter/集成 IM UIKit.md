<!--keywords: 快速开始,快速集成 IM UIkit,UIKit,IM UIKit,IMUIKit,Kit -->

网易云信 IM UIKit 是基于 [网易云信 IM SDK（NIM SDK）](https://doc.yunxin.163.com/messaging2/concept?platform=client) 开发的一款 [即时通讯 UI 组件库](https://doc.yunxin.163.com/messaging-uikit/concept/TI3NTgyNDA?platform=client)，功能涵盖了聊天、会话、群管理。本文介绍 Flutter 项目如何按照以下流程集成 10.x.x 版本的 IM UIKit。

```mermaid
graph LR
classDef default fill:#337EFF,stroke:#337EFF,stroke-width:0px,color:#FFFFFF;
按需导入组件 --> 添加权限 --> 配置会话模式 --> 初始化组件 --> 登录 --> 搭建界面
```

## 准备工作

在开始集成 IM UIKit 前，请确保您已完成以下操作：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，开通即时通讯 IM 服务，获取 App Key。
2. 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging2/guide/jU0Mzg0MTU?platform=client#第二步注册-im-账号)，获取账号 ID（`account_id`）和凭证（`token`）。
3. 准备如下开发环境：

    - Dart SDK 要求 3.5 及以上版本。如果需要兼容较低版本，请参考下文 [兼容低版本 Dart SDK](#compatibility)。
    - 支持的 CPU 架构：arm64-v8a、armeabi-v7a。（不支持 x86 模拟器。）
    - 项目开发环境：

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

## 第一步：按需导入组件

您可以根据业务需要，选择所需的 IM UIKit 组件。各组件相互独立，添加或删除均不影响项目编译。

::: note note
HarmonyOS 平台目前仅支持方式二，即通过源码依赖的方式导入。
:::

- **方式一**：如需添加远程依赖，在您的项目的 `pubspec.yaml` 中，添加相应组件。示例中的 `{LATEST_VERSION}`，建议使用最新版本，请参考 [更新日志](https://doc.yunxin.163.com/messaging-uikit/concept/jY4MjM0NDc)。

    :::::: div linked-codes
    ::: code 完整功能引入示例
    ```YAML
    dependencies:
        # 通讯录功能组件
        nim_contactkit_ui: ^{LATEST_VERSION}
        # 会话列表功能组件
        nim_conversationkit_ui: ^{LATEST_VERSION}
        # 群组功能组件
        nim_teamkit_ui: ^{LATEST_VERSION}
        # 聊天功能组件
        nim_chatkit_ui: ^{LATEST_VERSION}
        # 搜索功能组件
        nim_searchkit_ui: ^{LATEST_VERSION}
    ```
    :::
    ::: code 仅引入聊天示例
    ```YAML
    dependencies:
        # 会话列表功能组件
        nim_conversationkit_ui: ^{LATEST_VERSION}
        # 群组功能组件
        nim_teamkit_ui: ^{LATEST_VERSION}
        # 聊天功能组件
        nim_chatkit_ui: ^{LATEST_VERSION}
    ```
    :::
    ::::::

- **方式二**：如需添加本地依赖，请在获取对应的源码后，通过指定路径的形式实现。

    Flutter（Android & iOS） | Flutter（Android & iOS & HarmonyOS）
    :---: | :---: |
    `nim-uikit-flutter`<br>[GitHub 源码](https://github.com/netease-kit/nim-uikit-flutter) 或 [Gitee 源码](https://gitee.com/netease-yunxin/nim-uikit-flutter) | `nim-uikit-flutter-ohos`<br>[GitHub 源码](https://github.com/netease-kit/nim-uikit-flutter-ohos) 或 [Gitee 源码](https://gitee.com/netease-yunxin/nim-uikit-flutter-ohos)

    :::::: div linked-codes
    ::: code 完整功能引入示例
    ```YAML
    dependencies:
        # 通讯录功能组件
        nim_contactkit_ui:
            path: ../nim_contactkit_ui
        # 会话列表功能组件
        nim_conversationkit_ui:
            path: ../nim_conversationkit_ui
        # 群组功能组件
        nim_teamkit_ui:
            path: ../nim_teamkit_ui
        # 聊天功能组件
        nim_chatkit_ui:
            path: ../nim_chatkit_ui
        # 搜索功能组件
        nim_searchkit_ui:
            path: ../nim_searchkit_ui
    ```
    :::
    ::: code 仅引入聊天示例
    ```YAML
    dependencies:
        # 会话列表功能组件
        nim_conversationkit_ui:
            path: ../nim_conversationkit_ui
        # 群组功能组件
        nim_teamkit_ui:
            path: ../nim_teamkit_ui
        # 聊天功能组件
        nim_chatkit_ui:
            path: ../nim_chatkit_ui
    ```
    :::
    ::::::

## 第二步：添加权限

由于 IM UIKit 运行，需要拍摄/相册/录音/网络等权限，需要您在 Native 的文件中手动声明，才可正常使用相关能力。

:::::: div linked-codes
::: code Android
在 **android/app/src/main/AndroidManifest.xml** 的 `<manifest></manifest>`中，添加如下权限。

```
<uses-permission
    android:name="android.permission.INTERNET"/>
<uses-permission
    android:name="android.permission.RECORD_AUDIO"/>
<uses-permission
    android:name="android.permission.FOREGROUND_SERVICE"/>
<uses-permission
    android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission
    android:name="android.permission.VIBRATE"/>
<uses-permission
    android:name="android.permission.ACCESS_BACKGROUND_LOCATION"/>
<uses-permission
    android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission
    android:name="android.permission.READ_EXTERNAL_STORAGE"/>
<uses-permission
    android:name="android.permission.CAMERA"/>
<uses-permission 
    android:name="android.permission.READ_MEDIA_IMAGES"/>
<uses-permission 
    android:name="android.permission.READ_MEDIA_VIDEO"/>
```
::: 
::: code iOS
打开 **ios/Podfile**，在文件末尾新增如下权限代码。

```
post_install do |installer|
  installer.pods_project.targets.each do |target|
    flutter_additional_ios_build_settings(target)
    target.build_configurations.each do |config|        
          config.build_settings['EXCLUDED_ARCHS[sdk=iphonesimulator*]'] = 'arm64'               
          config.build_settings['ENABLE_BITCODE'] = 'NO'        
          config.build_settings["ONLY_ACTIVE_ARCH"] = "NO"    
        end
    target.build_configurations.each do |config|
          config.build_settings['GCC_PREPROCESSOR_DEFINITIONS'] ||= [
            '$(inherited)',
            'PERMISSION_MICROPHONE=1',
            'PERMISSION_CAMERA=1',
            'PERMISSION_PHOTOS=1',
            'PERMISSION_MEDIA_LIBRARY=1',
          ]
        end
  end
end
```
:::
::: code HarmonyOS
在鸿蒙项目 entry 目录下的 module.json5 文件中添加如下权限。

```
"requestPermissions": [
  {"name" :  "ohos.permission.INTERNET"},
  {
    "name" : "ohos.permission.CAMERA",
    "reason": "$string:Camera_reason",
    "usedScene": {
      "abilities": [
        "FormAbility"
      ],
      "when":"inuse"
    }
  },
  {
      "name": "ohos.permission.MICROPHONE",
      "reason": "$string:microphone_reason",
      "usedScene": {
        "abilities": [
            "EntryAbility"
          ],
        "when":"inuse"
      }
    }
]
```

::: note note
示例中的 `reason` 字段表示权限申请的原因说明，请自行在资源文件中定义该字符串。
:::
:::
::::::

## 第三步：配置会话存储模式

如果您的应用开通了 **高级版** 套餐，在初始化 SDK 之前，您可以选择会话是否存储在云端。入口为 IM UIKit 的核心类 `IMKitClient`，该类提供初始化、登录、获取当前账号信息等能力。

此步骤为可选，默认会话存储在本地。

```Dart
// 如果需要将会话存储在云端，设置为 true。默认为 false（存储在本地）
IMKitClient.setEnableCloudConversation(true);
```

关于云端会话功能的说明：

- **设置方法**：`IMKitClient.setEnableCloudConversation(true/false)`
- **获取当前设置**：`IMKitClient.enableCloudConversation`
- **默认值**：`false`（使用本地存储）

## 第四步：初始化 UIKit 和组件

在使用 IM UIKit 功能前，必须先对其进行初始化，但不需要对 IM UIKit 依赖的底层 [NIM SDK](https://doc.yunxin.163.com/messaging2/concept?platform=client) 单独初始化。初始化需要完成两部分：IM UIKit 的初始化和各功能组件的初始化。相关配置通过 [`NIMSDKOptions`](https://pub.dev/documentation/nim_core_v2_platform_interface/10.6.0/nim_core_v2_platform_interface/NIMSDKOptions-class.html) 添加。

1. 在应用的 `initState` 中初始化。

    ```Dart
    @override
    void initState() {
      super.initState();

      // 获取之前配置的会话存储模式
      final enableCloudConversation = await IMKitClient.enableCloudConversation;

      // 根据平台创建对应的 SDK 配置
      if (Platform.isAndroid) {
        options = NIMAndroidSDKOptions(
          appKey: "您的 App Key",
          enableV2CloudConversation: enableCloudConversation,
          // 其他配置...
        );
      } else if (Platform.isIOS) {
        options = NIMIOSSDKOptions(
          appKey: "您的 App Key",
          enableV2CloudConversation: enableCloudConversation,
          // 其他配置...
        );
      }

      // 初始化 IM UIKit
      IMKitClient.init(appKey, options).then((success) {
        if (success) {
          // 初始化成功
          print("IM UIKit 初始化成功");
        } else {
          // 初始化失败
          print("IM UIKit 初始化失败");
        }
      });
    }
    ```

2. 在应用的根 Widget 中初始化各功能组件。

    ```Dart
    class MyApp extends StatelessWidget {
      const MyApp({Key? key}) : super(key: key);

      // 初始化您需要的功能组件
      void initPlugins() {
        ChatKitClient.init();
        TeamKitClient.init();
        ConversationKitClient.init();
        ContactKitClient.init();
        SearchKitClient.init();
      }

      @override
      Widget build(BuildContext context) {
        // 初始化各功能组件
        initPlugins();

        return MaterialApp(
          title: 'IM UIKit',
          // 配置路由表
          routes: IMKitRouter.instance.routes,
          // 配置支持的语言
          supportedLocales: IMKitClient.supportedLocales,
          // 配置多语言委托
          localizationsDelegates: [
            CommonUILocalizations.delegate,
            ConversationKitClient.delegate,
            ChatKitClient.delegate,
            ContactKitClient.delegate,
            TeamKitClient.delegate,
            SearchKitClient.delegate,
            ...GlobalMaterialLocalizations.delegates,
          ],
          home: const MyHomePage(title: 'IM UIKit'),
        );
      }
    }
    ```

    如需了解更多配置方法，请参考 nim-uikit-flutter.git 项目中的 [config.dart](https://github.com/netease-kit/nim-uikit-flutter/blob/main/im_demo/lib/src/config.dart) 文件。

## 第五步：登录

在 UIKit 初始化成功后，调用 `IMKitClient.loginIM` 方法进行登录：

```Dart
// 将 account_id 和 token 替换为您的 IM 账号和凭证
IMKitClient.loginIM(NIMLoginInfo("account_id", "token")).then((success) {
    if (success) {
        // 登录成功
        print("IM 登录成功");
        // 如果需要使用呼叫组件，请在登录成功之后，初始化
        ChatKitClient.instance.setupCallKit(appKey: "your appkey", accountId: 'account');
    } else {
        // 登录失败
        print("IM 登录失败");
    }
});
```

:::note note
- 如果在初始化时已设置用户信息，初始化成功后还需调用 `getIt<IMLoginService>().syncUserInfo(account)` 方法同步用户信息。
- 如果需要使用呼叫组件，请在登录成功之后，初始化 CallKit。

    ```dart
    ChatKitClient.instance.setupCallKit(appKey: "your appkey", accountId: account);
    ```
:::

## 第六步：搭建界面

以搭建会话列表界面为例，您可以直接创建 `ConversationPage` 组件到您的应用中，还可以选择传入 `onUnreadCountChanged` 接口以获取当前未读消息数量信息。

```Dart
class _MyHomePageState extends State<MyHomePage> {
  int chatUnreadCount = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: ConversationPage(
        // 可选：监听未读消息数量变化
        onUnreadCountChanged: (unreadCount) {
          setState(() {
            chatUnreadCount = unreadCount;
          });
        },
      ),
    );
  }
}
```

会话列表界面最终搭建效果参考图如下：

<img style="width:55%;border: 1px solid #BFBFBF;" src="https://yx-web-nosdn.netease.im/common/bb0db82fe6013c2f197937c0dfe66880/FlutterUIKit会话列表.png"/>

## 下一步

IM UIKit 中提供的常用业务场景界面，创建或者跳转到界面需要传入具体参数，详情请参考 [界面跳转](https://doc.yunxin.163.com/messaging-uikit/guide/TI4NTgyODU?platform=flutter)，相关详细集成说明如下：

界面类 | 所属组件 | 界面介绍 | 参考文档
---- | ---- | ---- | ----
[`ConversationPage`](https://github.com/netease-kit/nim-uikit-flutter/blob/main/nim_conversationkit_ui/lib/page/conversation_page.dart) | nim_conversationkit_ui | 会话列表界面 | [集成会话列表界面](https://doc.yunxin.163.com/messaging-uikit/guide/DM1NzQyODM)
[`ContactPage`](https://github.com/netease-kit/nim-uikit-flutter/blob/main/nim_contactkit_ui/lib/page/contact_page.dart) | nim_contactkit_ui | 通讯录界面 | [集成通讯录界面](https://doc.yunxin.163.com/messaging-uikit/guide/DczNjExNDE)
[`ChatPage`](https://github.com/netease-kit/nim-uikit-flutter/blob/main/nim_chatkit_ui/lib/view/page/chat_page.dart) | nim_chatkit_ui | 单聊/群聊会话界面 | [集成会话消息界面](https://doc.yunxin.163.com/messaging-uikit/guide/jgyMzk2MDc)

## 常见问题

### 调试环境账号转为正式生产环境账号

为保障通信安全，如果您在调试环境中使用的是网易云信控制台生成的测试用 IM 账号和 token，请确保在后续的正式生产环境中，将其替换为通过 [IM 服务端 API](https://doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server) 生成的正式 IM 账号（account_id）和 token。

### 混合开发集成 IM UIKit 模拟器运行报错问题

因为 Google 兼容性问题，XCode 14 以上版本会出现该问题。为解决该问题，需要修改本地缓存文件。

在 **FlutterPluginRegistrant.podspec** 文件中添加以下内容进行模拟器支持配置：

```
s.pod_target_xcconfig = {
    'DEFINES_MODULE' => 'YES',
    'EXCLUDED_ARCHS[sdk=iphonesimulator*]' => 'i386 arm64'
}
```

::: note note 
由于上述修改的是本地缓存文件，因此，若您重新 `pod install`，需要重新修改本地的缓存文件。
:::

<a id="compatibility"></a>

### 兼容低版本 Dart SDK

- **extended_text_field 兼容**

    extended_text_field 是一个 Flutter 第三方组件库，用于提供增强的文本输入功能。网易云信 IM UIKit 依赖的 extended_text_field 组件需要匹配的具体版本。您在接入 IM UIKit 时，需要根据本地的 Dart SDK 版本匹配合适的 extended_text_field 版本，具体版本请参考 [extended_text_field 版本记录](https://pub.dev/packages/extended_text_field/versions)。例如：

    - Dart SDK 3.4 版本需要引入 extended_text_field 15.0.1 版本。
    - Dart SDK 3.3 版本需要引入 extended_text_field 14.0.1 版本。

    ```YAML
    dependency_overrides:
      # Dart 3.4
      extended_text_field: ^15.0.1
      # Dart 3.3
      # extended_text_field: ^14.0.1
    ```

- **intl 兼容**

    intl 是 Flutter 中用于国际化和本地化的核心库，提供日期格式化、消息翻译等功能。IM UIKit 默认依赖 intl V0.19.0 版本，如果您本地 Dart SDK 版本低于 3.4，可以通过 `dependency_overrides` 配置来降级使用 intl 0.18.0 版本，以确保兼容性。

    ```YAML
    // Dart SDK 版本低于 3.4，降级使用 intl 0.18.0 版本
    dependency_overrides:
      intl: ^0.18.0
    // Dart SDK 版本特定为 3.32.7，降级使用 intl 0.20.0 版本
    dependency_overrides:
      intl: ^0.20.0
    ```

- **flutter_markdown 兼容**

    flutter_markdown 是 Flutter 中用于渲染 Markdown 文本的库。IM UIKit 从 [10.2.0](https://doc.yunxin.163.com/messaging-uikit/concept/jY4MjM0NDc?platform=client#1020-2025-05-26) 版本起引入该依赖，默认依赖较新版本的 flutter_markdown。如果您本地 Dart SDK 版本低于 3.4，需要通过 `dependency_overrides` 配置来使用 flutter_markdown 0.7.4+3 版本，以确保兼容性。

    ```YAML
    dependency_overrides:
      flutter_markdown: 0.7.4+3
    ```

- **image_gallery_saver_plus 兼容**

    image_gallery_saver_plus 是 Flutter 中用于将图片、视频等媒体文件保存至设备的系统相册的核心库。IM UIKit 默认依赖 image_gallery_saver_plus V4.0.1 版本，如果您本地 Dart SDK 版本低于 3.5，可以通过 `dependency_overrides` 配置来降级使用 image_gallery_saver_plus V3.0.5，以确保兼容性。

    ```YAML
    dependency_overrides:
      image_gallery_saver_plus: ^3.0.5
    ```

### 兼容 go_router

[go_router](https://pub.dev/packages/go_router) 是 Flutter 官方支持的声明式路由包。UIKit 已适配 go_router，您可选择使用默认命名路由或 go_router。

::: note note
以下步骤需在所有组件初始化完成后调用。
:::

1. 启用 goRouter。

    ```dart
    IMKitRouter.instance.enableGoRouter = true;
    ```

2. 将 UIKit 的路由添加到 goRouter 配置中。

    ```dart
    // 路由初始化，添加自己的路由
    List<RouteBase> routes = [
      GoRoute(
        path: '/',
        builder: (BuildContext context, GoRouterState state) {
          return HomePage();
        },
      )//...
    ];

    // 添加 UIKit 的路由
    for (var element in IMKitRouter.instance.routes.entries) {
      routes.add(GoRoute(
          path: element.key,
          name:  element.key,
          builder: (BuildContext context, GoRouterState state) {
            return element.value(context);
          },
      )
      );
    }
    //路由设置
    _router = GoRouter(
      routes: routes,
      observers: [
        IMKitRouter.instance.routeObserver,
        NECallKitUI.navigatorObserver //呼叫组件，按需添加
      ],
    );
    ```

3. 将路由添加到 MaterialApp 中。

    ```dart
    MaterialApp.router(
      //...
      routerConfig: _router,
    )
    ```