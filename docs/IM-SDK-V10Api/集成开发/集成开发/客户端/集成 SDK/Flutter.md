网易云信即时通讯（NetEase IM）SDK V10（以下简称 NIM SDK）为 Flutter 开发者提供完善的即时通信功能开发能力，屏蔽其内部复杂细节，对外提供较为简洁的 API，方便您快速集成即时通信功能。

目前网易云信支持 Flutter 全平台（Android、iOS、MacOS、Windows、Web）的即时通讯 IM SDK，帮助您一套代码，全平台运行。本文介绍如何快速将 NIM Flutter SDK 集成到您的项目中。

::: note note 
本文主要介绍底层 Flutter SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 Flutter UIKit](https://doc.yunxin.163.com/messaging-uikit/guide?platform=flutter)。
:::

## 环境要求

集成 NIM Flutter SDK 前，请确保您的本地开发环境满足以下要求：

<style>
table th:first-of-type {width: 20%;}
table th:nth-of-type(2) {width: 20%;}
table th:nth-of-type(3) {width: 20%;}
table th:nth-of-type(4) {width: 20%;}
</style>

- **Dart SDK 版本**：3.0.0 ~ 4.0.0
- **Flutter SDK 版本** ：3.10.0 及以上版本
- **项目开发环境**：

    Android | iOS | macOS | Windows | Web | 鸿蒙
    ---- | ---- | ---- | ---- | ---- | ----
    <ul><li>Android Studio 3.5 及以上版本<li>Android 5.0 及以上版本设备<li>Kotlin Gradle Plugin 1.5.21 及以上版本 | <ul><li>Xcode 11.0 及以上版本<li>iOS 11.0 及以上版本设备<li>项目设置有效的开发者签名 | <ul><li>依赖 Python [Requests](https://pypi.org/project/requests/) 库<li>CMake 3.25.1 及以上版本 | 暂无环境要求 | 暂不支持 H5 | <ul><li>已配置 Flutter 鸿蒙开发环境（ 参考 [鸿蒙官方文档](https://gitcode.com/openharmony-tpc/flutter_flutter/tree/master)）<li>Flutter 版本使用 v3.27.5-ohos-0.0.2

## 集成 SDK

### 通过 Flutter 依赖

NIM Flutter SDK 已发布到 Dart 和 Flutter 项目提供包管理服务的平台 [pub.dev](https://pub.dev/) 库，您可以通过配置 `pubspec.yaml` 自动下载更新。

1. 在项目的 `pubspec.yaml` 文件中添加以下依赖。

    ```YAML
    dependencies:
    nim_core_v2: ^10.5.0
    ```

    ::: note note
    - 以上示例中的 10.5.0 可以更换为其他版本号，具体请参考 [更新日志](https://doc.yunxin.163.com/messaging2/concept/DMwMjA0MDI?platform=client)，推荐您使用最新版本的 SDK。
    - 鸿蒙版本接入方式采用 git 依赖，暂未上传至 pub。添加以下 git 依赖：

      ```yaml
      dependencies:
      nim_core_v2:
          git:
          url: "https://github.com/netease-kit/NIM-Flutter-SDK-OHOS.git"
      ```
    :::

2. 通过 Shell 或者 IDE 执行以下命令，下载依赖包。

    ```Bash
    flutter pub get
    ```

### 集成到 Web 平台

对于 Web 平台，您需要在 Flutter Web 项目的 `index.html` 文件中添加以下脚本引用：

1. 添加文件上传 SDK，例如 AWS SDK。

   ```HTML
   <script src="https://sdk.amazonaws.com/js/aws-sdk-2.410.0.min.js"></script>
   ```

2. 添加网易云信 IM SDK，例如 10.4.0 版本。

   ```HTML
   <script src="https://yx-web-nosdn.netease.im/package/1747194828266/index.umd_10_4_0.js?download=index.umd_10_4_0.js"></script>
   ```

3. 确保 `index.html` 包含必要的桥接代码，用于 Dart 和 JavaScript 之间的通信。

   ```JavaScript
   <script>
     window.s3 = AWS.S3
     window.onload = function () {
       // Flutter 初始化代码
       try {
         _flutter.loader
           .loadEntrypoint({
             serviceWorker: {
               // 需要您自行指定 serviceWorkerVersion，例如从 package.json 指定版本号
               serviceWorkerVersion: <yourServiceWorkerVersion>,
             },
           })
           .then(function (engineInitializer) {
             return engineInitializer.initializeEngine()
           }).then(appRunner => {
             window.$flutterWebGlobal = {
               rootService: new window.FlutterWeb.default(),
             }
             appRunner.runApp();
           })
       } catch (error) {
         console.log(error);
       }
     };

     async function dartCallNativeJs(callInfo = {}) {
       // JavaScript 桥接函数，允许 Dart 调用 JavaScript
       // 完整实现请参考完整示例
        const { serviceName, method, params, successCallback, errorCallback } =
            callInfo;
        try {
          console.log('dartCallNativeJs: ', callInfo)
          const service = window.$flutterWebGlobal.rootService[serviceName];
          if (!service) {
            throw new Error(`You do not implement this service: ${serviceName}`);
          }
          if (!service[method]) {
            throw new Error(`This method: ${method} is not implemented on this service: ${serviceName}`);
          } 
          // 参数中删除null       
          function removeNullValue(obj) {
            if (obj === null || obj === undefined) {
              return obj;
            }
            if (typeof obj === 'object') {
              Object.keys(obj).forEach(key => {
                if (obj[key] === null || obj[key] === undefined) {
                  delete obj[key];
                } else {
                  removeNullValue(obj[key]);
                }
              });
            }
            return obj;
          }
          removeNullValue(params);
          // 参数中删除serviceName
          if (params.hasOwnProperty('serviceName')) {
            delete params.serviceName;
          }
          const res = await service[method](params);
          successCallback(res)
        } catch (error) {
          console.error('dartCallNativeJs failed: ', error)
          errorCallback(error)
          throw error
        }
     }
   </script>
   ```

::: note note
Web 平台集成需要确保您的项目支持 Flutter Web，并且上述脚本正确加载到项目的 `index.html` 文件中。
:::

## 其他配置

### 运行 SDK [Windows]

::: note note
该步骤仅适用 Windows 平台，其他平台可直接跳过此步骤。
:::

将 SDK 复制到项目工程的 run 目录下，然后运行 SDK。

例如：将 `xxx\nim_core_v2\nim_core_v2_windows\nim_sdk\bin` 中的文件复制到 `xxx\nim_core_v2\nim_core_v2\example\build\windows\x64\runner\Debug` 中。

### 防混淆配置 [Android]

::: note note
该步骤仅适用 Android 平台，其他平台可直接跳过此步骤。
:::

1. 使用 `kotlin-gradle-plugin`，在工程根目录的 `build.gradle` 文件中添加以下配置。

    ```JSON
    buildscript {
        ext.kotlin_version = '1.9.0'
        repositories {
            google()
            mavenCentral()
        }

        dependencies {
            classpath 'com.android.tools.build:gradle:7.3.1'
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
        }
    }
    ```

2. 在 `app/build.gradle` 中，配置 `packagingOptions`，示例如下：

    ```Groovy
    / 新增：启用 kotlin 插件
        apply plugin: 'kotlin-android'

        android {
            // 其他配置
            ...

            packagingOptions {
                pickFirst 'lib/x86/libc++_shared.so'
                pickFirst 'lib/x86_64/libc++_shared.so'
                pickFirst 'lib/armeabi-v7a/libc++_shared.so'
                pickFirst 'lib/arm64-v8a/libc++_shared.so'
            }
        }
    ```

    ::: note note
    更多信息请参考 Android 的 [代码防混淆](https://doc.yunxin.163.com/messaging2/guide/DA5NzIyMjc?platform=client#第三步代码防混淆)。
    :::

## 下一步

完成 SDK 集成后，您可以尝试 [初始化](https://doc.yunxin.163.com/messaging2/guide/zY5NTAzMTI?platform=client)。

## 常见问题

### 编译错误 [Windows]

当编译项目时，出现类似以下报错信息时：

<img alt="Flutter 报错.png" src="https://yx-web-nosdn.netease.im/common/737a226c656ec6be31026d7879d562de/Flutter报错.png" style="width:80%;border: 1px solid #BFBFBF;">

您需要在 Windows 目录下的 **CMakeList.txt** 文件中添加以下代码，以解决上述问题。

```TXT
function(APPLY_STANDARD_SETTINGS TARGET)
  target_compile_features(${TARGET} PUBLIC cxx_std_17)
  target_compile_options(${TARGET} PRIVATE /W4 /WX- /wd"4100")
  target_compile_options(${TARGET} PRIVATE /EHsc)
  target_compile_definitions(${TARGET} PRIVATE "_HAS_EXCEPTIONS=0")
  target_compile_definitions(${TARGET} PRIVATE "$<$<CONFIG:Debug>:_DEBUG>")
endfunction()
```