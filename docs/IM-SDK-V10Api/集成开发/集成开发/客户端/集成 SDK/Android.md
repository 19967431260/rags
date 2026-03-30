<!-- keywords: 即时通讯,IM,基本功能,集成,集成 SDK,快速开始 -->

网易云信即时通讯 SDK（NetEase IM SDK，以下简称 NIM SDK）10.x.x+ 系列版本融合了低于 10.0.0 的接口，支持当前版本和低版本兼容两种模式。本文介绍如何快速将 NIM Android SDK 集成到您的 Android 项目中。

::: note note 
本文主要介绍底层 Android SDK 的集成，若您需要集成对应的 UI 组件，请参考 [集成 Android UIKit](https://doc.yunxin.163.com/messaging-uikit/guide/DU4NzAzNzQ?platform=android)。
:::

## 开发环境

- 系统要求：Android 5.0 及以上版本。
- 创建新项目：参考安卓官方文档 <a href="https://developer.android.com/studio/projects/create-project" target="_blank">创建 Android 项目</a>。
    :::details 单击点开查看创建 Android 新项目的步骤描述。
    1. 在顶部菜单依次选择 **File** > **New** > **New Project** 新建工程。
    2. 依次选择 **Phone and Tablet** > **Empty Activity**，单击 **Next**。

        <img style="width:50%" src="https://yx-web-nosdn.netease.im/common/d42430b47d5dc5a0f9c045bac02991cd/image.png" alt="image" />

    3. 创建项目后，Android Studio 会自动同步 Gradle。
    4. 同步成功后，即可开始集成 SDK。
    :::

## 第一步：集成 SDK

### 方式一：<span id="Gradle 集成">（推荐）Gradle 集成</span>

1. 在项目根目录的 `build.gradle` 文件中，配置 Maven 仓库。示例如下：

    ```Groovy
    allprojects {
        repositories {
            mavenCentral()
        }
    }
    ```

2. 在 `app` 目录下的 `build.gradle` 文件中，配置支持的 SO 库架构。示例如下：

    ```Groovy
    android {
    defaultConfig {
        ndk {
            //设置支持的 SO 库架构
            abiFilters "armeabi-v7a", "x86","arm64-v8a","x86_64"
            }
    }
    }
    ```

3. 根据项目需求，添加相应依赖。

    ::: note notice :::
    NIM SDK 各组件的版本号 **必须保持一致**。`${LATEST_VERSION}` 表示最新版本号，您可在 [SDK 更新日志](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 查看当前最新版本。
    :::

    ```Groovy
    dependencies {
        compile fileTree(dir: 'libs', include: '*.jar')
        // 添加依赖。注意，版本号必须一致。

        // 基础功能 (必需)
        implementation "com.netease.nimlib:basesdk:${LATEST_VERSION}"

        // 聊天室功能
        implementation "com.netease.nimlib:chatroom:${LATEST_VERSION}"

        // 厂商推送集成（小米、华为等）
        implementation "com.netease.nimlib:push:${LATEST_VERSION}"

        // 超大群功能
        implementation "com.netease.nimlib:superteam:${LATEST_VERSION}"

        // 全文检索插件
        implementation "com.netease.nimlib:lucene:${LATEST_VERSION}"
    }
    ```

### 方式二：<span id="手动集成">手动集成</span>

手动集成是指通过 [下载 SDK](https://doc.yunxin.163.com/messaging/resource?platform=android) 后，将其集成到工程项目中。

1. 在 <a href="https://doc.yunxin.163.com/messaging2/sdk-download" target="_blank">SDK 下载页面</a> 下载最新版本 SDK。

2. 将所需 SDK 文件拷贝至工程的 `libs` 目录下，完成配置。

    SDK 文件说明：

    ```Bash
    libs
    ├── arm64-v8a
    │   ├── libfusionstorage.so               //海外使用融合存储用户，必需
    │   ├── libhigh_available_android.so   //高可用功能库，必需
    │   ├── libne_audio.so                 //语音消息录制功能，必需
    │   ├── libtraceroute.so               //网络探测功能，必需
    │   ├── libartemis.so                  //网络探测功能，非必需
    ├── armeabi-v7a
    │   ├── libfusionstorage.so
    │   ├── libhigh_available_android.so
    │   ├── libne_audio.so
    │   ├── libtraceroute.so
    │   ├── libartemis.so
    ├── x86
    │   ├── libfusionstorage.so
    │   ├── libhigh_available_android.so
    │   ├── libne_audio.so
    │   ├── libtraceroute.so
    │   ├── libartemis.so
    ├── x86_64
    │   ├── libfusionstorage.so
    │   ├── libhigh_available_android.so
    │   ├── libne_audio.so
    │   ├── libtraceroute.so
    │   ├── libartemis.so
    │
    ├── nim-basesdk-x.x.x.jar       //IM 基础功能，必需
    ├── nim-chatroom-x.x.x.jar      //聊天室功能
    ├── nim-superteam-x.x.x.jar     //超大群功能
    ├── nim-avsignalling-x.x.x.jar   //信令功能
    ├── nim-lucene-x.x.x.jar        //全文检索插件
    ├── nim-push-x.x.x.jar          //通过网易云信集成设备厂商（例如小米手机）推送时需要
    ...
    ```

3. 在 `app/build.gradle` 文件中设置 `libs` 路径。

    ```Groovy
    android {
          ...
        compileOptions {
            // SDK 依赖的 JDK 版本为 Java 8
            sourceCompatibility JavaVersion.VERSION_1_8
            targetCompatibility JavaVersion.VERSION_1_8
        }
        ...

        dependencies {
            implementation fileTree(dir: "libs", include: ["*.jar"])
            ...
        }
    }
    ```
4. 单击 **File > Sync Project With Gradle Files**，等待同步完成。

## <span id="添加权限">第二步：配置权限</span>

权限配置根据代码设计的不同和兼容性区分了 V2 和 V1 两种模式，您选择的权限模式将影响后续的 [初始化](#init) 方式：

- V2 模式：适用于 [10.x.x 及以上](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 版本的全新配置方式。
- V1 模式：兼容 [10.0.0 以下](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client) 版本的配置方式。

根据应用需求，在 `AndroidManifest.xml` 中添加以下配置，注意替换：

- `com.netease.nim.demo`：替换为您的应用包名。
- `com.netease.nim.appKey`：可在此处配置，也可在 [初始化](#init) 时提供。`com.netease.nim.appKey` 需在 [网易云信控制台](https://app.yunxin.163.com/global/home) 通过 [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console) 获取。 

:::::: div linked-codes
::: code V2 模式（推荐）
```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.netease.nim.demo">

    <!-- 权限声明 -->
    <!-- 网络相关权限 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

    <application
        ...>
        <!-- AppKey 配置，可在此设置，也可在 SDKOptions 中提供
             若两处都提供，优先使用 SDKOptions 中的值 -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="key_of_your_app" />
        <!-- 云信后台服务声明 -->
        <service android:name="com.netease.nimlib.service.NimServiceV2" />
        
        <provider
                android:name="com.netease.nimlib.ipc.NIMContentProviderV2"
                android:authorities="${applicationId}.ipc.provider.v2"
                android:exported="false" />
    </application>
</manifest>
```
:::
::: code V1 兼容模式
```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.netease.nim.demo">

    <!-- 权限声明 -->
    <!-- 网络相关权限 -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />


    <application
        ...>
        <!-- AppKey 配置，可在此设置，也可在 SDKOptions 中提供
             若两处都提供，优先使用 SDKOptions 中的值 -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="key_of_your_app" />
        <!-- 云信后台服务声明 -->
        <service
                android:name="com.netease.nimlib.service.NimService"
                android:process=":core"
                />
        
        <service
                android:name="com.netease.nimlib.push.net.HeartbeatService"
                android:process=":core"
                />
        
        <!-- 云信后台辅助服务 -->
        <service
                android:name="com.netease.nimlib.job.NIMJobService"
                android:exported="false"
                android:permission="android.permission.BIND_JOB_SERVICE"
                android:process=":core"
                />
        
        <!-- 云信监听系统启动和网络变化的广播接收器，用于开机自启和网络变化时重新登录 -->
        <receiver
                android:name="com.netease.nimlib.service.NimReceiver"
                android:exported="false"
                android:process=":core"
                >
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
            </intent-filter>
        </receiver>
        
        <!-- 云信进程间通信组件 -->
        <receiver android:name="com.netease.nimlib.service.ResponseReceiver"
                />
        
        <service android:name="com.netease.nimlib.service.ResponseService"
                />
        
        <!-- 云信进程间通信 provider -->
        <provider
                android:name="com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider"
                android:authorities="${applicationId}.ipc.provider.preference"
                android:exported="false"
                />
        <provider
                android:name="com.netease.nimlib.ipc.NIMContentProvider"
                android:authorities="${applicationId}.ipc.provider"
                android:exported="false"
                android:process=":core"
                />
    </application>
</manifest>
```
:::
::::::

## <span id="混淆配置">第三步：代码防混淆</span>

代码混淆通过使用简短无意义的名称重命名现有类、方法和属性，增加逆向工程难度，保障应用代码安全。

为避免混淆导致调用 NIM SDK 出现异常，请在 `proguard-rules.pro` 文件中添加以下规则，将 NIM SDK 相关类排除在混淆范围外：

```ProGuard
-dontwarn com.netease.nim.**
-keep class com.netease.nim.** {*;}

-dontwarn com.netease.nimlib.**
-keep class com.netease.nimlib.** {*;}

-dontwarn com.netease.share.**
-keep class com.netease.share.** {*;}

-dontwarn com.netease.mobsec.**
-keep class com.netease.mobsec.** {*;}

#全文检索插件需要添加
-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}

#数据库功能需要添加
-keep class net.sqlcipher.** {*;}
-keep class net.zetetic.** { *; }
```

<a id="init"></a>

## 第四步：选择初始化方式

:::::: div linked-codes
::: code V2 模式（推荐）
V2 模式是 10.x.x+ 版本系列 NIM SDK 推荐的全新初始化方式，提供了更多功能和性能优化。使用 V2 模式需注意：

1. 初始化时调用 [NIMClient#initV2](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#aa8e0e524f223d29e8f2499557a2ae2e5) 方法。
2. [`AndroidManifest.xml`](#添加权限) 中仅需声明 V2 相关服务（`NimServiceV2` 和 `NIMContentProviderV2`）。
3. 初始化和参数配置需按照 V2 方式进行。详情请参考 [初始化 Android SDK](https://doc.yunxin.163.com/messaging2/guide/TY4OTgyMDk?platform=client)。
:::
::: code V1 兼容模式
如果需要保持与 10.0.0 以下版本 NIM SDK 的兼容性，可选择 V1 兼容模式：

1. 初始化时调用 [NIMClient#init](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1_n_i_m_client.html#a48056b399acd7f84ebcf5176b1cfde16) 方法。
2. [`AndroidManifest.xml`](#添加权限) 中需声明所有 V1 相关服务（`NimService`、`HeartbeatService` 等）。
3. 初始化和参数配置需按照 V1 方式进行，详情请参考 [初始化](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android)。
:::
::::::

## API 参考

您可以访问 [API 概览](https://doc.yunxin.163.com/console/docs/DY2Mjk0MjU?platform=client) 了解 NIM SDK 的完整 API 文档和使用方法。