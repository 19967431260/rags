Google 推送 FCM（Firebase Cloud Messaging）是谷歌推出的推送服务，支持海外用户推送离线消息，提供广泛的消息传递功能。

网易云信 IM 即时通讯 NIM SDK 自 4.6.0 之后的版本新增支持谷歌推送。

本文主要介绍如何接入谷歌厂商的离线推送通道，使消息通过谷歌推送服务离线推送至未在线的用户。

## 前提条件

谷歌推送 FCM 是 GCM 的升级版，适用于海外用户，FCM 成功推送需要 **两个条件**：

- **手机安装并成功运行谷歌移动框架**。
- **手机连接海外网络**。

    :::note notice
    - 在部分国产手机上，虽然满足以上两个条件，FCM 成功推送，但是推送通知栏可能未显示。
    - 如果应用面向国内用户，则不需要集成 FCM。
    :::

## 集成流程

### 步骤 1：在 Firebase 控制台创建项目

若已在 Firebase 平台创建项目并注册应用，则忽略该步骤。更多 FCM 推送服务的信息请参考 [Firebase 推送服务启用指南](https://firebase.google.cn/docs/android/setup?hl=zh-cn)。

1. 使用 Google 帐户 [登录 Firebase](https://console.firebase.google.com/?hl=zh-cn)。

2. 在 [Firebase 控制台](https://console.firebase.google.com/?hl=zh-cn) 创建一个 Firebase 项目。

    <details><summary>具体操作步骤</summary>

    1. 在 [Firebase 控制台](https://console.firebase.google.com/?hl=zh-cn)，单击 **添加项目**。
        - 如需将 Firebase 资源添加到现有 Google Cloud 项目，则输入该项目名称或从下拉菜单中选择该项目。
        - 如需要创建新项目，则输入项目名称。您还可以选择编辑项目名称下方显示的项目 ID。
    2. 如果出现提示，请查看并接受 Firebase 条款，然后单击 **继续**。
    3. 单击 **创建项目**。
        如果使用现有的 Google Cloud 项目，则单击 **添加 Firebase**。

    Firebase 会自动为您的 Firebase 项目配置资源。该过程完成后，您将转到 Firebase 控制台中 Firebase 项目的概览页面。
    </details>

3. 在 Firebase 项目中注册应用。

    <details><summary>具体操作步骤</summary>

    1. 在 Firebase 控制台中 Firebase 项目的概览页面，单击 **添加应用** 或 Android 图标启动设置工作流。
    2. 输入 Android 应用的相关信息后，单击 **注册应用**。

    </details>

<!--旧版

4. 注册完成后，获取应用的 AppID、AppKey、AppSecret，添加证书指纹。

    <details><summary>具体操作步骤</a></summary>

    1. 在[Firebase 控制台](https://console.firebase.google.com/?hl=zh-cn)，单击您的项目/Project，进入项目界面。
    2. 单击界面左上角的 **项目概览** 右侧的<img style="width:15px" src="https://yx-web-nosdn.netease.im/common/24fecd49736292a6a6ebbd3b89448a79/FirebaseProjectSettings.png" />，并单击 **项目设置**，进入项目设置界面。
    3. 如果您的项目设置界面上显示 Cloud Messaging API （旧版）已停用，则需要先启用 Cloud Messaging。
        1. 单击<img style="width:15px" src="https://yx-web-nosdn.netease.im/common/ebf0b6826d5917c326c7a63262be0bad/FireBaseOptionIcon.png" />，并单击 **在 Google Cloud Console 中管理 API**。

            <img alt="FireBaseProjectSettingsPage.png" src="https://yx-web-nosdn.netease.im/common/454735eeae439f09d79e0870e50b6e21/FireBaseProjectSettingsPage.png" style="width:80%;border: 1px solid #BFBFBF;">

        2. 填写信息，并启用 Cloud Messaging。

            <img alt="启用 CloudMessaging.png" src="https://yx-web-nosdn.netease.im/common/991b93b3ca12232e67787d266409db52/启用 CloudMessaging.png" style="width:80%;border: 1px solid #BFBFBF;">

    4. 单击 **云消息传递**，显示的服务器密钥即为所需的 AppSecret。

        <img alt="FireBase 服务器秘钥.png" src="https://yx-web-nosdn.netease.im/common/9ed7057e736ce91c58b85d1992d73b69/FireBase 服务器秘钥.png" style="width:80%;border: 1px solid #BFBFBF;">
    </details>
-->

### 步骤 2：在云信控制台添加 FCM 推送证书

您需要在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上提供 FCM 项目的服务账号授权凭证。网易云信支持新旧两种授权方式。

#### 新版：通过 JSON 格式私钥授权

1. 在 Firebase 控制台中，打开 **设置 > 服务账号**。
2. 单击 **生成新的私钥**。
3. 保存生成的包含私钥的 JSON 文件。

    <img alt="FCM.png" src="https://yx-web-nosdn.netease.im/common/24ae31211d860d4f3a57d0c3923f6c21/FCM.png" style="width:80%;border: 1px solid #BFBFBF;">

#### 旧版：通过服务器密钥授权

::: note notice
2020 年 3 月开始，FCM 已停止创建旧服务器密钥。详情请参考官方文档 [授权旧版协议发送请求](https://firebase.google.cn/docs/cloud-messaging/auth-server?hl=zh-cn#authorize-legacy-protocol-send-requests) 和 [迁移到 HTTP v1 API](https://firebase.google.cn/docs/cloud-messaging/migrate-v1?hl=zh-cn)。
:::

1. 在 Firebase 控制台中，打开 **设置 > 云消息传递**。
2. 记录 **服务器密钥**。

    <img alt="FireBase 服务器秘钥.png" src="https://yx-web-nosdn.netease.im/common/9ed7057e736ce91c58b85d1992d73b69/FireBase服务器秘钥.png" style="width:80%;border: 1px solid #BFBFBF;">

#### 上传至网易云信控制台

您需要将获取到的授权凭证上传至网易云信控制台：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 选择应用进入 **应用配置** 页面，单击 **证书管理** 页签。

2. 在 **Android 推送证书** 下单击 **添加证书**，选择证书类型为 **Google(FCM)**，配置谷歌推送相关信息。

    <img alt="谷歌推送.png" src="https://yx-web-nosdn.netease.im/common/5db002739ddadd32b3fefdb1ca767e10/谷歌推送.png" style="width:80%;border: 1px solid #BFBFBF;">

    <table>
        <thead>
            <tr> <th>网易云信推送证书字段</th><th>对应 Firebase 应用的字段信息</th></tr></thead>
                <tr> <td> 证书名称</td><td>用户自定义推送证书名称，最大 32 字符。</br>对应初始化 NIM SDK 时需传入的推送证书信息中的 fcmCertificateName。</td></tr>
                <tr> <td> 应用包名</td><td>对应 Firebase 应用的 <strong>软件包名称</strong>，最大 1000 字符。</td></tr>
                <tr> <td> AppSecret</td><td>对应 Firebase 应用的 <strong>服务器密钥</strong>，最大 5000 字符。<note type=note>若添加方式选择 <b>上传证书</b>，则忽略该字段，直接上传证书即可。</td></tr>
    </table>

3. 根据界面提示，在该对话框内配置证书类型和证书名称等信息。

### 步骤 3：添加 Firebase 配置文件

1. 在 Firebase 项目中注册应用，单击 **下载 google-services.json** 获取 Firebase 配置文件。
2. 将配置文件添加至应用的 `app` 根目录下。
3. 若需要在应用中启用 Firebase，则需要将 [google-services 插件](https://developers.google.cn/android/guides/google-services-plugin?hl=zh-cn) 添加到 Gradle 文件中。
    - 在项目级 Gradle 文件 (build.gradle)中配置 Google 的 Maven 代码库，以导入 Google 服务 Gradle 插件。

        ```Groovy
        buildscript {

        repositories {
        // Make sure that you have the following two repositories
        google() // Google's Maven repository
        mavenCentral() // Maven Central repository
            }

        dependencies {
        ...

        // Add the dependency for the Google services Gradle plugin
        classpath 'com.google.gms:google-services:4.3.15'
            }
        }

        allprojects {
        ...

        repositories {
            // Make sure that you have the following two repositories
            google() // Google's Maven repository
            mavenCentral() // Maven Central repository
            }
        }
        ```

    - 在应用级 Gradle 文件（app/build.gradle）中，添加 Google 服务 Gradle 插件：

        ```Groovy
        plugins {
        id 'com.android.application'

        // Add the Google services Gradle plugin
        id 'com.google.gms.google-services'
        ...
        }
        ```

### 步骤 4： 导入 Firebase SDK

NIM SDK 当前兼容的荣耀推送版本请参考 [更新日志](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client) 中的 **第三方推送兼容版本**。

1. 在应用级 Gradle 文件（app/build.gradle）中，增加 FCM 推送 Firebase SDK 相关依赖和 Google 推送依赖。

    ```Groovy
    dependencies {
    // firebase-messaging
    implementation 'com.google.firebase:firebase-messaging:24.0.0'
    // firebase-analytics
    implementation 'com.google.firebase:firebase-analytics:22.0.0'
    }
    ```

2. 同步您的应用以确保所有依赖项都具有所需的版本。

### 步骤 5：权限配置

在 `app/src/main` 目录中，打开 `AndroidManifest.xml` 配置文件，添加对应权限。

```XML
<!-- fcm -->
<service android:name="com.netease.nimlib.mixpush.fcm.FCMTokenService">
    <intent-filter>
        <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
    </intent-filter>
</service>
```

您还可以设置收到 FCM 通知展示的图标和颜色。

```XML
android:resource="@drawable/改成您的通知图标" />
<meta-data
android:name="com.google.firebase.messaging.default_notification_color"
android:resource="@color/改成您的通知字体颜色" />
```

如果您的应用使用了代码混淆，在 `proguard-rules.pro` 配置文件中添加以下配置以防止 FCM SDK 的代码被混淆：

```
-dontwarn com.google.**
-keep class com.google.** {*;}
```

## 平台限制

本章节介绍谷歌推送 FCM 平台的限制。

### 消息类型

使用 FCM，您可以向客户端发送两种类型的消息：

- 通知消息（显示消息）。由 FCM SDK 自动处理。
- 由客户端应用程序处理的数据消息。

通知消息包含一组预定义的用户可见键。相比之下，数据消息仅包含用户定义的自定义键值对。通知消息可以包含可选的数据负载。两种消息类型的最大负载均为 4000 字节，但从 Firebase 控制台发送消息时除外，它强制执行 1024 个字符的限制。

消息类型 | 使用场景 | 如何发送 |
---- | ---- | ---- |
通知消息 | FCM 代表客户端应用程序自动向最终用户设备显示消息。通知消息具有一组预定义的用户可见键和自定义键值对的可选数据负载。 | <ol><li>在 Cloud Functions 或您的应用程序服务器等受信任的环境中，使用 Admin SDK 或 FCM 服务器协议：设置 notification 键。可能有可选的数据负载。总是可折叠的。查看显示通知和发送请求负载的一些示例。</li><li>使用通知编辑器：输入消息文本、标题等，然后发送。通过提供自定义数据来添加可选的数据负载。</li></ol>
数据信息 | 客户端应用程序负责处理数据消息。数据消息只有自定义键值对，没有保留键名。 | 在 Cloud Functions 或您的应用程序服务器等受信任的环境中，使用 Admin SDK 或 FCM 服务器协议：仅设置 data 密钥。 |

### 消息推送类型配置

为了确保推送能正常提醒用户，需设置推送消息的类型 `android_channel_id`，该字段的配置可通过网易云信 NIM SDK 中消息体的 `pushPayload` 来实现。

**示例代码**：

```Java
// fcmField 结构示例
//     "fcmField": {
//         "android_channel_id":""
//     }

pushPayload.put("pushTitle", "Set push title here");
pushPayload.put("fcmField", fcmField);
```

:::note note
对于传给 FCM 推送平台的消息类型有以下逻辑：
- 您上传的消息体的 `pushPayload` 中有分类（android_channel_id）字段，则使用 `pushPayload` 中的字段值。
- 如果消息体的 `pushPayload` 中未传入分类（android_channel_id）字段，则使用网易云信默认的推送消息类型（android_channel_id="0"），若需要修改网易云信默认的推送消息类型请联系商务经理或技术支持。
:::

### 推送消息自定义配置

在网易云信 NIM SDK 的消息体 [V2NIMMessage](https://doc.yunxin.163.com/messaging2/references/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1v2_1_1message_1_1_v2_n_i_m_message.html) 的 `V2NIMMessagePushConfig.pushPayload` 字段可配置一个 key 为 `fcmField`，值为 map 或者 JSONObject 的 Entry，实现推送标题、图标等配置。具体的值请参考 [谷歌 FCM 官方文档](https://firebase.google.cn/docs/reference/fcm/rest/v1/projects.messages?hl=zh-cn#androidnotification)。

示例代码如下：

```JSON
{
  "title": string,//通知的标题
  "body": string,//通知的正文
  "icon": string,//通知的图标
  "color": string,//通知的图标颜色
  "sound": string,//通知的提示声音
  "tag": string,//通知的标识符
  "click_action": string,//通知的单击跳转
  "image": string,//通知中的图片 URL
  ...
}
```

### 设置消息的优先级

您有两个选项可以为下游消息分配传递优先级：普通优先级和高优先级。虽然跨平台的行为略有不同，但普通和高优先级消息的传递如下：

- 普通优先级：当设备未休眠时，普通优先级消息会被立即传递。当设备处于低电耗模式时，此类消息可能会被延迟传递以节省电量，直到设备退出低电耗模式。对于时间敏感度较低的消息，例如新电子邮件通知、保持 UI 同步或在后台同步应用程序数据，请选择普通优先级。
- 高优先级：FCM 会立即尝试传递高优先级消息，允许 FCM 在必要时唤醒休眠设备并运行一些有限的处理（包括非常有限的网络访问）。高优先级消息通常应该会导致用户与您的应用或其通知进行互动。高优先级消息用于时间敏感的、用户可见的内容。

### 上行消息限制

- 将每个项目的 [上行消息](https://firebase.google.com/docs/cloud-messaging/android/upstream?hl=zh-cn) 限制为 1500000 条/分钟，以避免上游目标服务器过载。
- 将每台设备的上行消息限制为 1000 条/分钟，以防止电池因不良应用行为而耗尽。

### 主题消息限制

主题订阅添加/移除速率限制为每个项目 3000 QPS。
有关消息发送速率，请参考 《Firebase 官方文档》 [扇出限制](https://firebase.google.com/docs/cloud-messaging/concept-options?hl=zh-cn#fanout_throttling)。