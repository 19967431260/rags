<!-- keywords: 即时通讯,IM,基本功能,集成,集成 SDK,快速开始 -->

本文介绍如何快速将网易云信 IM SDK（NetEase Instant Messaging SDK，NIM SDK）集成到您的 Android 项目中。

## 开发环境

- Android 5.0 及以上版本。
- 自 v6.9.0 起，改用 AndroidX 支持库，Target API 改为 28，不再支持 support 库。

## 第一步：集成 SDK

NIM SDK 支持两种集成方式：

- 通过 Gradle 自动集成（推荐）。

- 通过 [下载 SDK](https://doc.yunxin.163.com/messaging/resource)，然后手动集成到您的工程项目中。

### 方式一：**<span id="Gradle 集成">Gradle 集成</span>**

1. 若您需要创建新项目，在 Android Studio 里，在顶部菜单依次选择 **File** > **New** > **New Project** 新建工程，再依次选择 **Phone and Tablet** > **Empty Activity**，单击 **Next**。

    <img style="width:50%" src="https://yx-web-nosdn.netease.im/common/5c330c3371274f9cb714a48f8865d3bc/android_create_project.png" alt="image" />

    ::: note note
    [创建 Android 项目](https://developer.android.com/studio/projects/create-project) 成功后，Android Studio 会自动开始同步 gradle, 您需要等同步成功后再进行下一步操作。
    :::

2. 在项目根目录下的 **build.gradle** 文件中，配置 `repositories`（使用 maven）。示例代码如下：

    ```Groovy
    allprojects {
        repositories {
            mavenCentral()
        }
    }
    ```

3. 在 **app** 目录下的 **build.gradle** 文件中，配置支持的 SO 库架构。示例代码如下：

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

4. 根据开发者项目的需求，添加对应的依赖。

    ::: note notice :::
    - NIM SDK 组件版本号 **必须一致**。您可在 [SDK 更新日志](https://doc.yunxin.163.com/messaging/guide/DM1MjI5MTE?platform=android) 中查看当前最新版本。
    - [NIM SDK 稳定版](https://doc.yunxin.163.com/messaging/guide/Dk4MzgzOTE?platform=android) 暂未支持如下列出的 **全文检索插件**。
    :::

    ```Groovy
    dependencies {
        compile fileTree(dir: 'libs', include: '*.jar')
        // 添加依赖。注意，版本号必须一致。

        // 基础功能 (必需)
        implementation "com.netease.nimlib:basesdk:${LATEST_VERSION}"

        // 聊天室需要
        implementation "com.netease.nimlib:chatroom:${LATEST_VERSION}"

        // 通过网易云信来集成小米等厂商推送需要
        implementation "com.netease.nimlib:push:${LATEST_VERSION}"

        // 超大群需要
        implementation "com.netease.nimlib:superteam:${LATEST_VERSION}"

        // 全文检索插件
        implementation "com.netease.nimlib:lucene:${LATEST_VERSION}"

        // 海外融合存储需要
        // 该功能仅支持 Gradle 集成，不提供手动集成方式
        implementation "com.netease.nimlib:fusionstorage:${LATEST_VERSION}"
        implementation "com.google.code.gson:gson:${GSON_VERSION}" // Gson 推荐版本 2.8.9
    }
    ```

### 方式二：<span id="手动集成">手动集成</span>

1. 若您需要创建新项目，在 Android Studio 里，在顶部菜单依次选择 **File** > **New** > **New Project** 新建工程，再依次选择 **Phone and Tablet** > **Empty Activity**，单击 **Next**。

    <img style="width:50%" src="https://yx-web-nosdn.netease.im/common/5c330c3371274f9cb714a48f8865d3bc/android_create_project.png" alt="image" />

    ::: note note
    [创建 Android 项目](https://developer.android.com/studio/projects/create-project) 成功后，Android Studio 会自动开始同步 gradle, 您需要等同步成功后再进行下一步操作。
    :::

2. 在 [SDK 下载页面](https://doc.yunxin.163.com/messaging/resource) 下载最新版本的 SDK。

3. 按需将对应的 SDK 文件拷贝至工程的 `libs` 目录下，即可完成配置。

    ::: note notice
    [NIM SDK 稳定版](https://doc.yunxin.163.com/messaging/guide/Dk4MzgzOTE?platform=android) 暂未支持如下列出的 **全文检索插件**。
    :::

    SDK 文件说明如下：

    ```
    libs
    ├── arm64-v8a
    │   ├── libne_audio.so          //语音消息录制功能，必需
    │   ├── traceroute.so           //网络探测功能，必需
    │   ├── libc++_shared.so        //C++ 动态库，必需
    │   ├── libhigh-available.so    //高可用功能库，必需
    ├── armeabi-v7a
    │   ├── libne_audio.so
    │   ├── traceroute.so
    │   ├── libc++_shared.so
    │   ├── libhigh-available.so
    ├── x86
    │   ├── libne_audio.so
    │   ├── traceroute.so
    │   ├── libc++_shared.so
    │   ├── libhigh-available.so
    ├── x86_64
    │   ├── libne_audio.so
    │   ├── traceroute.so
    │   ├── libc++_shared.so
    │   ├── libhigh-available.so
    │
    ├── nim-basesdk-x.x.x.jar       //IM 基础功能，必需
    ├── nim-chatroom-x.x.x.jar      //聊天室功能
    ├── nim-lucene-x.x.x.jar        //全文检索插件
    ├── nim-push-x.x.x.jar          //通过网易云信集成小米等厂商推送时需要

    ```
3. 在 **app/build.gradle** 文件中设置 **libs** 路径。

    ```Java
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
4. 单击 <b>File > Sync Project With Gradle Files</b> 按钮，直到同步完成。

## 第二步：添加权限

您可以根据实际应用需求，设置所需的权限。

在 `AndroidManifest.xml` 中添加以下配置：

::: note note
您可在 `AndroidManifest.xml` 中配置网易云信的 App Key，也可在 [初始化](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android#步骤2初始化-sdk) 时配置。App Key 通过在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上 [创建应用](https://doc.yunxin.163.com/messaging/guide/TEwMDY3NzQ?platform=android) 获取。
:::

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.netease.nim.demo">

    <!-- 权限声明 -->
    <!-- 访问网络状态-->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />


    <application
        ...>
        <!-- App key, 可以在这里设置，也可以在 SDKOptions 中提供。
            如果 SDKOptions 中提供了，则取 SDKOptions 中的值。-->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="key_of_your_app" />
		<!-- 声明云信后台服务 -->
		<service
				android:name="com.netease.nimlib.service.NimService"
				android:process=":core"
				/>
		
		<service
				android:name="com.netease.nimlib.push.net.HeartbeatService"
				android:process=":core"
				/>
		
		<!-- 声明云信后台辅助服务 -->
		<service
				android:name="com.netease.nimlib.job.NIMJobService"
				android:exported="false"
				android:permission="android.permission.BIND_JOB_SERVICE"
				android:process=":core"
				/>
		
		<!-- 云信SDK的监视系统启动和网络变化的广播接收器，用户开机自启动以及网络变化时候重新登录 -->
		<receiver
				android:name="com.netease.nimlib.service.NimReceiver"
				android:exported="false"
				android:process=":core"
				>
			<intent-filter>
				<action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
			</intent-filter>
		</receiver>
		
		<!-- 云信进程间通信receiver -->
		<receiver android:name="com.netease.nimlib.service.ResponseReceiver"
				/>
		
		<!-- 云信进程间通信service -->
		<service android:name="com.netease.nimlib.service.ResponseService"
				/>
		
		<!-- 云信内部使用的进程间通信provider -->
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

## 第三步：代码防混淆

代码混淆是指使用简短无意义的名称重命名已存在的类、方法、属性等，增加逆向工程的难度，保障 Android 程序源码的安全性。

为了避免因上述的重命名而导致调用 NIM SDK 异常，请在 proguard-rules.pro 文件中加入以下代码，将 NIM SDK 相关类加入不混淆名单。

```Groovy
-dontwarn com.netease.nim.**
-keep class com.netease.nim.** {*;}

-dontwarn com.netease.nimlib.**
-keep class com.netease.nimlib.** {*;}

-dontwarn com.netease.share.**
-keep class com.netease.share.** {*;}

-dontwarn com.netease.mobsec.**
-keep class com.netease.mobsec.** {*;}

#如果您使用全文检索插件，需要加入
-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}

#如果您开启数据库功能，需要加入
-keep class net.sqlcipher.** {*;}
-keep class net.zetetic.** { *; }
```

## 下一步

- 完成 SDK 集成后，需进行 [初始化](https://doc.yunxin.163.com/messaging/guide/TI5ODE2MTM?platform=android)。
- 您可在 [Android SDK API](https://doc.yunxin.163.com/messaging/guide/zg0MzYzNzY?platform=android) 了解 SDK API 的基础信息（接口类型、返回值类型和调用框架），查看核心 API 列表和核心类列表。

## Demo 参考

网易云信在 Github 上提供了 [开源的 IM Demo](https://github.com/netease-kit/nim-uikit-android)，为您后续的 IM 集成提供参考。