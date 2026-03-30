<!--keywords: 快速开始,快速集成 IM UIkit,UIKit,demo,IM UIKit,IMUIKit,Kit -->

网易云信 IM UIKit 是基于 NIM SDK（网易云信 IM SDK）开发的一款 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TI3NTgyNDA?platform=android" target="_blank">即时通讯 UI 组件库</a>，包括聊天、会话、群管理等组件。本文介绍如何快速跑通 IM UIKit 的集成流程。

## 前提条件

在开始集成 IM UIKit 前，请确保您已：

- 已在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上，[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 App Key。
- 已 [注册 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-注册-im-账号)，获取账号 ID（`account_id`）和凭证（Token）。

- **准备如下开发环境/工具**：
    - Android Studio Bumblebee
    - Java 11
    - Gradle 7.4.1
    - Android Gradle Plugin 7.1.3
    - Android v7.0 及以上版本

## 注意事项

由于 IM UIKit 的初始化与登录是通过底层调用 NIM SDK 接口来实现的，因此重复调用 IM UIKit 和 NIM SDK 的初始化与登录接口会相互覆盖传入的信息（包括 **推送配置信息**）。

所以若用户同时集成 IM UIKit 和 NIM SDK，只需要调用一次初始化与登录接口即可。

## 第一步：按需导入组件

根据业务需要，在您的项目的 `build.gradle` 中，以添加依赖的形式添加相应的 IM UIKit 组件和第三方库（Glide、Retrofit 和 OkHttp）。各组件相互独立，添加或删除均不影响项目编译。

例如，需要通讯录功能和会话列表功能，可添加 `contactkit-ui` 和 `conversationkit-ui`。

```Groovy
dependencies {
    // 通讯录功能
    implementation("com.netease.yunxin.kit.contact:contactkit-ui:${LATEST_VERSION}")
    // 会话列表功能组件
    implementation("com.netease.yunxin.kit.conversation:conversationkit-ui:${LATEST_VERSION}")
    // 群组功能组件
    implementation("com.netease.yunxin.kit.team:teamkit-ui:${LATEST_VERSION}")
    // 聊天功能组件
    implementation("com.netease.yunxin.kit.chat:chatkit-ui:${LATEST_VERSION}")
    // 位置消息功能组件
    implementation("com.netease.yunxin.kit.locationkit:locationkit:${LATEST_VERSION}")
    // 图片库
    implementation("com.github.bumptech.glide:glide:4.13.1")
    // 网络库
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.squareup.retrofit2:converter-gson:2.9.0")
    implementation("com.squareup.retrofit2:converter-scalars:2.9.0")
    implementation("com.squareup.okhttp3:okhttp:4.9.3")
}
```

**添加权限**

根据实际应用需求，在 AndroidManifest.xml 文件中设置所需的权限。

<details><summary>添加所需权限</summary>

```XML
<?xml version="1.0" encoding="utf-8"?>
<!-- 请将 com.netease.nim.demo 替换为自己的包名 -->
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.netease.nim.demo">

    <!-- 权限声明 -->
    <!-- 访问网络状态-->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />

    <uses-permission android:name="android.permission.CHANGE_WIFI_STATE"/>

    <!-- 外置存储存取权限 -->
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>

    <!-- 多媒体相关 -->
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.RECORD_AUDIO"/>
    <!-- Android11：V8.6.1及之后的版本不需要；其他：V4.4.0及之后的版本不需要 -->
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>

    <!-- 控制呼吸灯，振动器等，用于新消息提醒 -->
    <uses-permission android:name="android.permission.FLASHLIGHT" />
    <uses-permission android:name="android.permission.VIBRATE" />

    <!-- 8.0+系统需要-->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />

    <!-- 下面的 uses-permission 一起加入到您的 AndroidManifest 文件中。-->
    <permission
        android:name="com.netease.nim.demo.permission.RECEIVE_MSG"
        android:protectionLevel="signature"/>

     <uses-permission android:name="com.netease.nim.demo.permission.RECEIVE_MSG"/>

    <application
        ...>
        <!-- App key, 可以在这里设置，也可以在 SDKOptions 中提供。
            如果 SDKOptions 中提供了，则取 SDKOptions 中的值 -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="key_of_your_app" />

        <!-- 云信后台服务，请使用独立进程 -->
        <service
            android:name="com.netease.nimlib.service.NimService"
            android:process=":core"/>

       <!-- 云信后台辅助服务 -->
        <service
            android:name="com.netease.nimlib.service.NimService$Aux"
            android:process=":core"/>

        <!-- 云信后台辅助服务 -->
        <service
            android:name="com.netease.nimlib.job.NIMJobService"
            android:exported="false"
            android:permission="android.permission.BIND_JOB_SERVICE"
            android:process=":core"/>

        <!-- 网易云信监视系统启动和网络变化的广播接收器，保持和 NimService 同一进程 -->
        <receiver android:name="com.netease.nimlib.service.NimReceiver"
            android:process=":core"
            android:exported="false">
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE"/>
            </intent-filter>
        </receiver>

        <!-- 网易云信进程间通信 Receiver -->
        <receiver android:name="com.netease.nimlib.service.ResponseReceiver"/>

        <!-- 网易云信进程间通信 service -->
        <service android:name="com.netease.nimlib.service.ResponseService"/>

        <!-- 网易云信进程间通信 provider -->
        <provider
            android:name="com.netease.nimlib.ipc.NIMContentProvider"
            android:authorities="com.netease.yunxin.app.im.ipc.provider"
            android:exported="false"
            android:process=":core" />

          <!-- 网易云信内部使用的进程间通信 provider -->
          <!-- SDK 启动时会强制检测该组件的声明是否配置正确，如果检测到该声明不正确，SDK 会主动抛出异常引发崩溃 -->
        <provider
            android:name="com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider"
            android:authorities="com.netease.yunxin.app.im.ipc.provider.preference"
            android:exported="false" />
    </application>
</manifest>
```

</details>

**防止代码混淆**

代码混淆是指使用简短无意义的名称重命名已存在的类、方法、属性等，增加逆向工程的难度，保障 Android 程序源码的安全性。

为了避免因上述的重命名而导致调用 IM UIKit 异常，请在 proguard-rules.pro 文件中加入以下代码，将 NIM SDK 和 IM UIKit 的相关类加入不混淆名单。

<details><summary>防混淆</summary>

```
## NIM SDK 防混淆

-dontwarn com.netease.nim.**
-keep class com.netease.nim.** {*;}

-dontwarn com.netease.nimlib.**
-keep class com.netease.nimlib.** {*;}

-dontwarn com.netease.share.**
-keep class com.netease.share.** {*;}

-dontwarn com.netease.mobsec.**
-keep class com.netease.mobsec.** {*;}

## IM UIKit 防混淆

-dontwarn com.netease.yunxin.kit.**
-keep class com.netease.yunxin.kit.** {*;}
-keep public class * extends com.netease.yunxin.kit.corekit.XKitInitOptions
-keep class * implements com.netease.yunxin.kit.corekit.XKitService {*;}

## 呼叫组件防混淆

-keep class com.netease.lava.** {*;}
-keep class com.netease.yunxin.** {*;}

-dontwarn com.netease.yunxin.kit.**
-keep class com.netease.yunxin.kit.** {*;}
-keep public class * extends com.netease.yunxin.kit.corekit.XKitInitOptions
-keep class * implements com.netease.yunxin.kit.corekit.XKitService {*;}

## 高德 3D 地图

-keep   class com.amap.api.maps.**{*;}
-keep   class com.autonavi.**{*;}
-keep   class com.amap.api.trace.**{*;}

## 高德定位

-keep class com.amap.api.location.**{*;}
-keep class com.amap.api.fence.**{*;}
-keep class com.loc.**{*;}
-keep class com.autonavi.aps.amapapi.model.**{*;}

## glide 4

-keep public class * implements com.bumptech.glide.module.GlideModule
-keep public class * extends com.bumptech.glide.module.AppGlideModule
-keep public enum com.bumptech.glide.load.resource.bitmap.ImageHeaderParser$** {
    **[] $VALUES;
    public *;
}

## okhttp

-dontwarn okhttp3.**
-keep class okhttp3.**{*;}

## 如使用全文检索插件则需添加以下代码

-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}

## 如开启数据库功能则需添加以下代码

-keep class net.sqlcipher.** {*;}
```

</details>

::: note note
更多组件导入的说明，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TgzMDcyMzc?platform=android" target="_blank">组件导入</a>。
:::

## 第二步：初始化

1. 在 `AndroidManefest.xml` 中配置 App Key。

    如果需要使用**发送地理位置消息**的功能，还需在 `AndroidManefest.xml` 中配置高德地图 API Key 和定位服务（APSService）。

    示例代码如下：

    ```Java
    <!-- 在 application 节点里面增加<meta-data>配置网易云信 APPKey 等 -->
    <application ...>
        <meta-data
            android:name="com.netease.nim.appKey"
            <!-- 传入您的网易云信 App Key -->
            android:value="your APPKey" />
        <!-- 高德地图 API Key -->
        <meta-data
            android:name="com.amap.api.v2.apikey"
            <!-- 传入您的高德地图 API Key -->
            android:value="apikey" />
        <!-- 高德地图定位 -->
        <service android:name="com.amap.api.location.APSService" />
    </application>

    ```
    ::: note note
    高德地图 API Key 的具体获取方式，参考 [高德开放平台文档](https://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key)。
    :::

2. 在 IM UIKit 项目的 IMApplication 的 `onCreate` 中添加如下代码。

    ```Java
    public class IMApplication extends MultiDexApplication {
        @Override
        public void onCreate() {
            super.onCreate();
            // 在 Application 的 onCreate 中添加
            SDKOptions options = new SDKOptions();
            //填入 APPKEY
            options.appKey = "App KEY";
            //如果有 account 和 token 信息可以填入登录信息直接进行登录
            LoginInfo loginInfo = LoginInfo.LoginInfoBuilder.loginInfoDefault("account", "token").build();
            IMKitClient.init(this,loginInfo,options);

            if (IMKitUtils.isMainProcess(this)) {
                //位置消息模块需要初始化
                LocationKitClient.init();
            }
        }
    }

    ```

    ::: note note
    更多初始化说明，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/jY3MDA4NzY?platform=android" target="_blank">初始化</a>。
    :::

## 第三步：登录

::: note notice
如果登录信息（<a href="https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html" target="_blank">`LoginInfo`</a>）在初始化的时候已传入，则不需要再进行本节内容介绍的登录步骤。
:::

如果不能在 Applicatiton 中获取登录信息 `LoginInfo`，需调用 `IMKitClient` 类中的 `loginIM` 方法登录：

方法名 | 参数 | 说明
:---- | :---- | :----
`loginIM` | <a href="https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html" target="_blank">`LoginInfo`</a> | 与 IM 服务端建立长连接，登录 IM

调用登录的方法时，将如下示例代码中的 `accid` 和 `token` 分别替换为您的网易云信账号 ID （即 accid）和 Token。

```Java
LoginInfo loginInfo = LoginInfo.LoginInfoBuilder.loginInfoDefault("accid","token").build();
IMKitClient.loginIM(loginInfo,new LoginCallback<LoginInfo>() {
    @Override
    public void onError(int errorCode, @NonNull String errorMsg) {
        //登录失败
    }

    @Override
    public void onSuccess(@Nullable LoginInfo data) {
        //登录成功
    }
});
```

## 第四步：界面搭建

网易云信 IM UIKit 提供两套风格的 [UI 组件库](https://doc.yunxin.163.com/messaging-uikit/guide/TI3NTgyNDA?platform=android)，可任意选择一种使用。两种风格的界面流程如下：

:::::: div linked-codes
::: code 基础版 UI 界面

以搭建会话列表界面为例，基本流程如下（更多详情参考下文的 [界面集成详情](#界面集成详情)）：

1. 在您应用中需要添加会话列表界面的 Activity 下创建 `conversationFragment`。

    示例代码如下：

    ```Java
    ConversationFragment conversationFragment = new ConversationFragment();
    ```

2. 将 `conversationFragment` 添加到这个 Activity 中。

    ```Java
        FragmentManager fragmentManager = getSupportFragmentManager();
        //R.id.container 您添加界面的 GroupLayout
        fragmentManager
            .beginTransaction().add(R.id.container, conversationFragment)
            .commit();
    ```
    ::: note notice
    上述示例代码中的 `getSupportFragmentManager` 方法属于 Android Activity 的默认方法，如果您使用 Android X 中的 `AddCompatActivity` 则可以直接调用该方法。如果您使用的是 `android.app.acitivity`，则需要调用 `getFragmentManager` 方法。
    :::

    最终集成效果参考下图：

    <img style="width:80%" src="https://yx-web-nosdn.netease.im/common/11707474727796454a82bfdf823f5534/960主要模块.png" />

:::
::: code 通用版 UI 界面

以搭建会话列表界面为例，基本流程如下（更多详情参考下文的 [界面集成详情](#界面集成详情)）：

1. 在您应用中需要添加会话列表界面的 Activity 下创建 `FunConversationFragment`。

    示例代码如下：

    ```Java
    FunConversationFragment conversationFragment = new FunConversationFragment();
    ```

2. 将 `conversationFragment` 添加到这个 Activity 中。

    ```Java
        FragmentManager fragmentManager = getSupportFragmentManager();
        //R.id.container 您添加界面的 GroupLayout
        fragmentManager
            .beginTransaction().add(R.id.container, conversationFragment)
            .commit();
    ```
    ::: note notice
    上述示例代码中的 `getSupportFragmentManager` 方法属于 Android Activity 的默认方法，如果您使用 Android X 中的 `AddCompatActivity` 则可以直接调用该方法。如果您使用的是 `android.app.acitivity`，则需要调用 `getFragmentManager` 方法。
    :::

    最终集成效果参考下图：

    <img style="width:80%" src="https://yx-web-nosdn.netease.im/common/1d225879d3f6eda6e3a8027462f3dc60/960主要模块绿.png" />

:::
::::::

## 下一步

为保障通信安全，如果您在调试环境中的使用的是网易云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/TM5MzM5Njk/docs/DQ3Nzk1MTY?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`accid`）和 `token`。

## 相关参考

### 界面集成详情

IM UIKit 中提供的常用业务场景界面及相关详细集成说明如下：

:::::: div linked-codes
::: code 基础版 UI 界面

界面 | 所属组件 | 描述
:---- | :---- | :----
`ConversationFragment` | `conversationkit-ui` | 会话列表界面（创建或者跳转到该界面需要传入参数，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/DUxNDczMjg?platform=android" target="_blank">集成会话列表界面</a>）
`ContactFragment` | `contactkit-ui` | 通讯录界面 （创建或者跳转到该界面需要传入参数，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/zY2NDgxMzI?platform=android" target="_blank">集成通讯录界面</a>）
`ChatP2PFragment`/`ChatP2PActivity` | `chatkit-ui` | 单聊会话界面（创建或者跳转到该界面需要传入参数，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TcyNzQwMDg?platform=android" target="_blank">集成会话消息界面</a>）
`ChatTeamFragment`/`ChatTeamActivity` | `chatkit-ui` | 群聊会话界面（创建或者跳转到该界面需要传入参数，请参考 <a href="https://doc.yunxin.163.com/messaging-uikit/guide/TcyNzQwMDg?platform=android" target="_blank">集成会话消息界面</a>）

:::
::: code 通用版 UI 界面

界面 | 所属组件 | 描述
:---- | :---- | :----
`FunConversationFragment` | `conversationkit-ui` | 会话列表界面
`FunContactFragment` | `contactkit-ui` | 通讯录界面
`FunChatP2PFragment`/`FunChatP2PActivity` | `chatkit-ui` | 单聊会话界面
`FunChatTeamFragment`/`FunChatTeamActivity` | `chatkit-ui` | 群聊会话界面

:::
::::::

### 音视频通话

集成会话界面后，如果需要在会话界面实现音视频通话功能，请参考 [实现音视频通话](https://doc.yunxin.163.com/messaging-uikit/guide/Dk5ODUxMTA?platform=android)。

<!--

### 使用原生 SDK 中方法

如果您需要在 IM UIKit 中自行实现目前 UIKit 还未实现，但原生 IM Android SDK 已提供的能力。您可以通过调用原生 IM Android SDK 中提供的接口来实现。例如，您想对 IM UIKit 的消息历史进行全文检索，可以调用原生 IM Android SDK 中的 方法，示例代码如下：

```
```

原生 IM Android SDK 中的接口请参考对应的 [API 文档](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/annotated.html)。
-->

### UIKit 版本升级

若由于业务需求需要升级 UIKit，在升级时请参考 [UIKit 版本升级说明](https://doc.yunxin.163.com/messaging-uikit/guide/jE1NzQ4OTc?platform=android)。

### 系统兼容相关

如果项目中的 SdkVersion 采用 Android 13（33），那么需要修改其中的权限申请，这样才能正常使用图片和文件发送功能。具体请参考 [Android 13 文件权限适配](https://doc.yunxin.163.com/messaging-uikit/guide/jQwNjc5MzA?platform=android#android-13-文件权限适配)。

### 常见问题排查

集成过程中的常见问题的排查说明，请参考 [IM UIKit 常见问题排查](https://doc.yunxin.163.com/messaging-uikit/guide/DE2MDc3NTM?platform=android)。