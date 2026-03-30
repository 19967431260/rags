<!--keywords: 快速开始,快速集成 IM UIkit,UIKit,demo,IM UIKit,IMUIKit,Kit -->
  

网易云信圈组 UIKit（QChat UIKit）是基于 NetEase Instant Messaging SDK（以下简称 NIM SDK）中的圈组模块开发的一款[圈组 UI 组件库]()。本文介绍如何集成圈组 UIKit 到您的即时通讯项目中。


## 前提条件

在开始集成圈组 UIKit 前，请确保：

- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)，获取 AppKey。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-注册-im-账号)，获取 accid 和 Token。

- 准备如下开发环境/工具：
    - [Android Studio Bumblebee](https://developer.android.com/studio/archive?hl=zh-cn)
    - Java 11
    - Gradle 7.4.1
    - Android Gradle Plugin 7.1.3
    - Android v7.0 及以上版本

## 实现流程

@startuml
!theme cerulean
(*) -right-> "按需导入组件"
-right-> "初始化"
-right-> "登录"
-right-> "界面搭建"
-right-> (*)
@enduml
  
  
### 步骤1 按需导入组件

在您的项目的 `build.gradle` 中，以添加依赖的形式添加相应的圈组 UIKit 组件（qchatkit-ui）和第三方库（Glide）。同时，根据业务需要，您也可以引入 [IM UIKit 组件库](https://doc.yunxin.163.com/messaging-uikit/guide/TI3NTgyNDA?platform=android)（例如需要通讯录功能和会话列表功能，可添加 `contactkit-ui` 和 `conversationkit-ui`）。各组件相互独立，添加或删除均不影响项目编译。

```groovy
dependencies { 
    implementation("com.netease.yunxin.kit.qchat:qchatkit-ui:${LATEST_VERSION}")
}
```

**添加权限**

根据实际应用需求，在 AndroidManifest.xml 文件中设置所需的权限。

<details><summary>添加所需权限</summary>

```xml
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

    <!-- 替换 com.netease.yunxin.app.qchat 为您自己的包名 -->

    <!-- 下面的 uses-permission 一起加入到你的 AndroidManifest 文件中。 -->
    <permission
        android:name="com.netease.yunxin.app.qchat.permission.RECEIVE_MSG"
        android:protectionLevel="signature"/>

    <uses-permission android:name="com.netease.yunxin.app.qchat.permission.RECEIVE_MSG"/>

    <application
        ...>
        <!-- AppKey 可以在这里设置，也可以在 SDKOptions 中提供。
            如果 SDKOptions 中提供了，则取 SDKOptions 中的值。 -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="key_of_your_app" />

        <!-- 云信后台服务，请使用独立进程。 -->
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

        <!-- 云信监视系统启动和网络变化的广播接收器，保持和 NimService 同一进程 -->
        <receiver android:name="com.netease.nimlib.service.NimReceiver"
            android:process=":core"
            android:exported="false">
            <intent-filter>
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE"/>
            </intent-filter>
        </receiver>

        <!-- 云信进程间通信 Receiver -->
        <receiver android:name="com.netease.nimlib.service.ResponseReceiver"/>

        <!-- 云信进程间通信service -->
        <service android:name="com.netease.nimlib.service.ResponseService"/>

    <!-- 替换 com.netease.yunxin.app.qchat 为您自己的包名 -->

        <!-- 云信进程间通信provider -->
        <provider
            android:name="com.netease.nimlib.ipc.NIMContentProvider"
            android:authorities="com.netease.yunxin.app.qchat.ipc.provider"
            android:exported="false"
            android:process=":core" />
      	
      	<!-- 云信内部使用的进程间通信provider -->
      	<!-- SDK启动时会强制检测该组件的声明是否配置正确，如果检测到该声明不正确，SDK会主动抛出异常引发崩溃 -->
        <provider
            android:name="com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider"
            android:authorities="com.netease.yunxin.app.qchat.ipc.provider.preference"
            android:exported="false" />
    </application>
</manifest>
```

</details>

**防止代码混淆**

代码混淆是指使用简短无意义的名称重命名已存在的类、方法、属性等，增加逆向工程的难度，保障 Android 程序源码的安全性。

为了避免因上述的重命名而导致使用圈组 UIKit 异常，请在 `proguard-rules.pro` 中加入以下代码，将 NIM SDK 和圈组 UIKit 的相关类加入不混淆名单。

<details><summary>防混淆</summary>

```
# NIM SDK 防混淆
-dontwarn com.netease.nim.**
-keep class com.netease.nim.** {*;}

-dontwarn com.netease.nimlib.**
-keep class com.netease.nimlib.** {*;}

-dontwarn com.netease.share.**
-keep class com.netease.share.** {*;}

-dontwarn com.netease.mobsec.**
-keep class com.netease.mobsec.** {*;}

# 圈组 UIKit 防混淆
-dontwarn com.netease.yunxin.kit.**
-keep class com.netease.yunxin.kit.** {*;}
-keep public class * extends com.netease.yunxin.kit.corekit.XKitInitOptions
-keep class * implements com.netease.yunxin.kit.corekit.XKitService {*;}

# 呼叫组件防混淆 （）
-keep class com.netease.lava.** {*;}
-keep class com.netease.yunxin.** {*;}

# 高德地图 V5.0.0之后：
-keep   class com.amap.api.maps.**{*;}
-keep   class com.autonavi.**{*;}
-keep   class com.amap.api.trace.**{*;}

# 高德地图定位
-keep class com.amap.api.location.**{*;}
-keep class com.amap.api.fence.**{*;}
-keep class com.loc.**{*;}
-keep class com.autonavi.aps.amapapi.model.**{*;}

##高德地图搜索
-keep   class com.amap.api.services.**{*;}


# glide 4
-keep public class * implements com.bumptech.glide.module.GlideModule
-keep public class * extends com.bumptech.glide.module.AppGlideModule
-keep public enum com.bumptech.glide.load.resource.bitmap.ImageHeaderParser$** {
    **[] $VALUES;
    public *;
}

# 如使用全文检索插件则需添加以下代码
-dontwarn org.apache.lucene.**
-keep class org.apache.lucene.** {*;}

# 如开启数据库功能则需添加以下代码
-keep class net.sqlcipher.** {*;}
```

</details>

::: note note
更多组件导入的说明，请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/TgzMDcyMzc?platform=android" target="_blank">组件导入</a>。
:::

### 步骤2 初始化


1. 在 `AndroidManefest.xml` 中配置您在云信控制台获取的 [AppKey](https://doc.yunxin.163.com/console/docs/TIzMDE4NTA?platform=console)。

    如果需要使用“发送地理位置消息”的功能，还需在 `AndroidManefest.xml` 中配置高德地图 API Key 和定位服务（APSService）。

    示例代码如下：

    ```xml 
    <!-- 在 application 节点中增加 <meta-data> 配置云信 AppKey 等 -->
    <application ...>
        <meta-data
            android:name="com.netease.nim.appKey"
            <!-- 传入您的云信 AppKey -->
            android:value="your AppKey" /> 
    </application>
    ```

2. 在圈组 UIKit 项目的 Application 的 `onCreate` 中添加如下代码（可参考[圈组 Demo 源码](https://github.com/netease-kit/qchat-uikit-android)中 `QChatApplication` 中的初始化示例代码）。

    ```java
    public class QChatApplication extends MultiDexApplication {
        @Override
        public void onCreate() {
            super.onCreate();
            // 在Application的onCreate中添加
            SDKOptions options = new SDKOptions();
            //填入APPKEY
            options.appKey = "APP KEY";
            QChatKitClient.init(this, null, options);
        }
    }
    ```

    ::: note note
    更多初始化说明，请参见<a href="https://doc.yunxin.163.com/messaging-uikit/guide/jY3MDA4NzY?platform=android" target="_blank">初始化</a>。
    :::


### 步骤3 登录

::: note notice
如果登录信息（<a href="https://doc.yunxin.163.com/messaging/references/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_login_info.html" target="_blank">`LoginInfo`</a>）在 SDK 初始化时已传入，则可以跳过本步骤。 
:::

<br>

如果不能在 Application 中获取登录信息 `LoginInfo`，则需要调用 `QChatKitClient.loginIMWithQChat` 方法完成云信 IM 和云信圈组登录：

方法名 | 参数 | 说明
:---- | :-------------- | :---------
`loginIMWithQChat` | <a href="https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/classcom_1_1netease_1_1nimlib_1_1sdk_1_1qchat_1_1param_1_1_q_chat_login_param.html" target="_blank">`QChatLoginParam`</a> | 与 IM 服务端建立长连接，登录圈组


调用登录的方法时，将如下示例代码中的 `accid` 和 `token` 分别替换为您的[云信 IM 账号（即 `accid`）和 Token](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-%E6%B3%A8%E5%86%8C-im-%E8%B4%A6%E5%8F%B7)。 


```java
LoginInfo loginInfo = LoginInfo.LoginInfoBuilder.loginInfoDefault("accid","token").build();
QChatKitClient.loginIMWithQChat(loginInfo,new LoginCallback<QChatLoginResult>() {
    @Override
    public void onError(int errorCode, @NonNull String errorMsg) {
        //登录失败
    }

    @Override
    public void onSuccess(@Nullable QChatLoginResult data) {
        //登录成功
    }
});

```



### 步骤4 界面搭建

通过圈组 UIKit 搭建界面的基本流程如下：

1. 在您应用中需要添加圈组界面的 Activity 下创建一个 `QChatServerFragment`。

    示例代码如下：

    ```java 
    QChatServerFragment qChatFragment = new QChatServerFragment();
    ```

2. 将 `QChatServerFragment` 添加到该 Activity 中。

    ```java 
        FragmentManager fragmentManager = getSupportFragmentManager();
        //R.id.container 你添加界面的GroupLayout
        fragmentManager
            .beginTransaction().add(R.id.container, qChatFragment)
            .commit();
    ```
    ::: note notice 
    上述示例代码中的 `getSupportFragmentManager` 方法属于 Android Activity 的默认方法，如果您使用 Android X 中的 `AddCompatActivity` 则可以直接调用该方法。如果您使用的是 `android.app.acitivity`，则需要调用 `getFragmentManager` 方法。
    :::


## 后续步骤

为保障通信安全，如果您在调试环境中的使用的是云信控制台生成的测试用 IM 账号 和 `token`，请确保在后续的正式生产环境中，将其替换为通过 <a href="https://doc.yunxin.163.com/TM5MzM5Njk/docs/DQ3Nzk1MTY?platform=server" target="_blank">IM 服务端 API</a> 生成的正式 IM 账号（`accid`）和 `token`。


