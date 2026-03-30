网易云信 IM 即时通讯服务基于网易多年的通信服务技术积累，致力于打造最稳定的即时通讯平台。NetEase Instant Messaging Flutter SDK（以下简称为 NIM Flutter SDK）为 Flutter 应用提供完善的即时通信功能开发框架，屏蔽其内部复杂细节，对外提供较为简洁的 API，方便您的应用快速集成即时通信功能。

:::note note 
NIM Flutter SDK 目前支持 Android 和 iOS。非移动端（包括 Windows、macOS 和 Web）仍为 Beta 版本，处于内测阶段，敬请期待。
:::



## 开发环境

请确保您的开发环境，满足如下要求：





- Flutter-dart 2.17.0 及以上版本。
- 各端开发环境要求：
    :::::: div custom-tabs
    ::: tab Android
    - Android Studio 3.5 及以上版本。
    - App 要求 Android 4.4 API 19 及以上版本设备。
    - 1.5.21以上版本的 `kotlin-gradle-plugin`。
    :::
    ::: tab iOS
    - Xcode 11.0 及以上版本。
    - App 要求 iOS 11.0 以上版本设备。
    - 项目已设置有效的开发者签名。
    :::
    <!--
    ::: tab Windows (Beta)
    - 操作系统：Windows 7 SP1 或更高的版本（基于 x86-64 的 64 位操作系统）。
    - 安装 Visual Studio 2019。
    - 安装 CMake 3.10及以上版本。
    :::
    ::: tab macOS (Beta)
    - Xcode 11.0 及以上版本。
    - App 要求 macOS 10.14 及以上版本。
    - 项目已设置有效的开发者签名。
    :::
    ::: tab Web (Beta)
    - 已安装 VSCode, 且在 VSCode 中安装 flutter 插件。
    - 已能熟练使用 Flutter 命令。
    :::
    -->
    ::::::
    

    ::: note note
    Windows、macOS 和 Web 目前仍为 Beta 版本，处于内测阶段，敬请期待。
    :::
## 集成SDK


NIM Flutter SDK 已经发布到 pub 库，您可以通过配置 `pubspec.yaml` 自动下载更新。


1. 在项目的 `pubspec.yaml` 文件中添加以下依赖。

    ```
    dependencies: 
    nim_core: ^1.1.0 
    ```

    

2. 通过 Shell 或者 IDE 执行以下命令，下载依赖包。

    ```
    flutter pub get
    ```

<!--Web 端集成

1. 在项目的 `pubspec.yaml` 文件中添加以下依赖。
    ```
    dependencies: 
    nim_core: ^1.1.0 
    ```
2. 通过 Shell 或者 IDE 执行以下命令下载依赖包：

    ```
    flutter pub get
    ```


3. Web 端集成需要在与各端平级的目录创建一个 web 文件夹，并在该 web 文件夹下创建 index.html 文件，文件内容模板如下：


    ::: note important
    如下模板中的链接是云信 IM Flutter Web SDK 的前端 js 资源包的链接，每次版本升级需替换成最新版本的链接，最新版本链接请联系技术支持获取。
    :::

    ```
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8" />
        <meta content="IE=Edge" http-equiv="X-UA-Compatible" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta
        name="description"
        content="Flutter web"
        />
        <title>您的页面标题名称</title>
        <script>
        // The value below is injected by flutter build, do not touch.
        var serviceWorkerVersion = null;
        </script>
        <script src="flutter.js"></script>
    </head>
    <body>
        <script>
        //如下链接是云信 IM flutter web sdk的前端 js 资源包，每次版本升级需替换成最新版本的链接，最新版本链接请联系技术支持获取
        var jsConfig = [
            "https://yx-web-nosdn.netease.im/package/1664415864168/index.0.0.6.umd.js",
        ];

        window.onload = function () {
            // Download main.dart.js
            try {
            _flutter.loader
                .loadEntrypoint({
                serviceWorker: {
                    serviceWorkerVersion: serviceWorkerVersion,
                },
                })
                .then(function (engineInitializer) {
                return engineInitializer.initializeEngine()
                }).then(appRunner => {
                require(jsConfig, (RootService) => {
                    window.$flutterWebGlobal = {
                    rootService: new RootService.default(),
                    }
                    appRunner.runApp();
                });
                })
            } catch (error) {
            console.log(error);
            }
        };

        async function dartCallNativeJs(callInfo = {}) {
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
    </body>
    </html>
    ```

4. 执行`flutter run -d chrome`命令测试集成是否成功。执行后能看到如下入口页面和 Chrome 控制台调用日志，则表示集成成功。


    ![FlutterWeb集成成功.png](https://yx-web-nosdn.netease.im/common/8791d62a5745b0c51cfa5641e7e6372e/FlutterWeb集成成功.png)


-->




## 编译与防混淆配置（仅 Android）




集成 SDK 之后，Android 端还需要额外添加以下配置。

### **编译配置**
1. 使用`kotlin-gradle-plugin`，在工程根目录的 `build.gradle` 文件中添加以下配置。

    ```groovy
    //file: build.gradle

    buildscript {
        ext.kotlin_version = '1.5.21'
        repositories {
            google()
            mavenCentral()
        }

        dependencies {
            classpath 'com.android.tools.build:gradle:4.1.3'
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
        }
    }
    ```

2. 在 `app/build.gradle` 中配置 `packagingOptions`，示例如下：

    ```groovy
        //file: app/build.gradle

        // 新增：启用 kotlin 插件
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

### **防混淆配置**


代码混淆是指使用简短无意义的名称重命名已存在的类、方法、属性等，增加逆向工程的难度，保障 Android 程序源码的安全性。

为了避免因上述的重命名而导致调用 NIM SDK 异常，请在 proguard-rules.pro 文件中加入以下代码，将 NIM Flutter SDK 相关类加入不混淆名单。


<img src="https://yx-web-nosdn.netease.im/common/98385bad2067cee4a541037cb2aea738/Flutter防混淆文件路径.png" style="width:400px" />



```groovy
-dontwarn com.netease.**
-keep class com.netease.** {*;}
-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}
-keep class net.sqlcipher.** {*;}
```
