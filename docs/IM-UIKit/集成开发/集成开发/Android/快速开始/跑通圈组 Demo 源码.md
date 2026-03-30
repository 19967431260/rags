网易云信在 GitHub 上提供开源的圈组 Demo 源码。您可参考 Demo 源码，在您的本地项目中快速构建即时通讯应用。


本文介绍如何快速跑通圈组 Demo 源码。


## 前提条件


在开始运行示例项目之前，请确保您已：

- 已通过[功能概览](https://doc.yunxin.163.com/messaging-uikit/guide/Dk1MjU4MjM?platform=android)了解圈组相关基础概念和功能。
- 已在云信控制台[创建应用](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console)，获取 App Key。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-注册-im-账号)，获取 accid 和 token。

    
- 准备如下开发环境/工具：

    - [Android Studio Bumblebee](https://developer.android.com/studio/archive?hl=zh-cn)
    - Java 11 及以上
    - Gradle 7.4.1 及以上
    - Android Gradle Plugin 7.1.3 及以上

## 跑通步骤

1. 前往 GitHub <a href="https://github.com/netease-kit/qchat-uikit-android" target="_blank">下载圈组 Demo 源码</a>。
    
2. 使用 Android studio 打开示例项目。
    在菜单栏中选择 **File > Open**，选择示例项目源码仓库（例如 `netease-kit/qchat-uikit-android`）所在目录。

3. 在 `AndroidManifest.xml` 文件中配置云信 [AppKey](https://doc.yunxin.163.com/console/guide/TIzMDE4NTA?platform=console#获取-appkey-和-appsecret)。
    
    示例代码：

    ```
    <!--在 application 节点中增加 <meta-data>，用于配置云信 AppKey 等-->
        <application ...>
        <!-- 云信 APPKEY -->
        <meta-data
            android:name="com.netease.nim.appKey"
            android:value="your AppKey" /> 
    </application>
    ```

    如果需要使用圈组 UIKit 中“发送地理位置消息”的功能，还需在 `AndroidManefest.xml` 中配置[高德地图 API Key](https://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key) 和定位服务（APSService）。 

    示例代码：
    ```
    <!--在 application 节点中增加 <meta-data>，用于配置高德地图 API Key 等-->
        <application ...>
        <!-- 高德地图API Key -->
        <meta-data
            android:name="com.amap.api.v2.apikey"
            android:value="apikey" />  
        <!-- 高德地图定位 -->
        <service android:name="com.amap.api.location.APSService" />
    </application>
    ```
4. 配置 IM 账号（accid）和 Token。

    在 `WelcomActivity` 中的 `startLogin` 方法后填入您[注册](https://doc.yunxin.163.com/messaging-uikit/guide/Dc0NjI1MTA?platform=android#4-注册-im-账号)的 IM 账号和 Token。

    示例代码：

    ```
    private void startLogin() {

        String account = ""; // 传入 IM 账号（accid）
        String token = ""; // 传入 Token 
        LoginInfo loginInfo = LoginInfo.LoginInfoBuilder.loginInfoDefault(account,token).build();

        if (!TextUtils.isEmpty(account) && !TextUtils.isEmpty(token)) {
            loginQChatAndIM(loginInfo);
        } else {
            activityWelcomeBinding.appDesc.setVisibility(View.GONE);
            activityWelcomeBinding.loginButton.setVisibility(View.VISIBLE);
            activityWelcomeBinding.loginButton.setOnClickListener(view -> launchLoginPage());
        }
    }
    ```

5. 将示例项目运行在您的 Android 设备上，即可开始体验圈组相关功能。

## 参考信息

本工程包含 Demo（app）和圈组 UIKit 源码，Demo 默认采用 Maven 方式引入`QChatkit-ui`（圈组模块）。如果想修改为源码依赖，请在 `app/build. gradle` 文件中修改依赖方式即可。