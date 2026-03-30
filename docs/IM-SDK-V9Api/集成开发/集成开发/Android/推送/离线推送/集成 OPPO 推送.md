网易云信 IM 即时通讯 NIM SDK 自 6.7.0 之后的版本新增支持 OPPO 推送。

本文主要介绍如何集成 OPPO 厂商的离线推送通道，使消息通过 OPPO 推送服务离线推送至未在线的用户。

## 第一步：并启用推送服务

**若已在 OPPO 开放平台创建应用，则忽略该步骤。更多 OPPO 推送服务的信息请参考 [OPPO 推送服务开启指南](https://open.oppomobile.com/new/developmentDoc/info?id=10195)。**

1. 在 [OPPO 开放平台](https://open.oppomobile.com) 注册开发者账号并完成认证，详情请参考 [OPPO 企业开发者账号注册流程](https://open.oppomobile.com/new/developmentDoc/info?id=10446)。

2. 登录 [OPPO 开放平台](https://open.oppomobile.com)，创建应用，具体请参考 [应用接入流程](https://open.oppomobile.com/new/developmentDoc/info?id=10035)。

3. 应用创建完成后，在开放平台，依次选择 **产品–移动服务–推送服务**，进入 [推送服务产品页](https://open.oppomobile.com/new/introduction?page_name=push)，单击 **立即使用**。

4. 进入推送运营平台，单击 **申请推送服务**。

    <img alt="OPPO 申请推送服务.png" src="https://yx-web-nosdn.netease.im/common/3acbb0a5756d2e08448da48e159835a7/OPPO申请推送服务.png" style="width:60%;border: 0px solid #BFBFBF;">

5. 在 **未开启服务** 中选择需要申请 PUSH 权限的应用，进入 PUSH 服务并单击 **申请开通**。

    <img alt="OPPO 未开启服务.png" src="https://yx-web-nosdn.netease.im/common/aaf154a2bc72c350c39237e1e8ea9717/OPPO未开启服务.png" style="width:60%;border: 0px solid #BFBFBF;">

    <img alt="OPPO 申请开通.png" src="https://yx-web-nosdn.netease.im/common/92a37eacff6b46ab5577bd0eff1f1c1f/OPPO申请开通.png" style="width:60%;border: 0px solid #BFBFBF;">

6. 填写申请信息后，提交申请，等待审核通过。

    <img alt="OPPO 提交申请.png" src="https://yx-web-nosdn.netease.im/common/39b6ff69103eb013a690e01bbb8aca32/OPPO提交申请.png" style="width:60%;border: 0px solid #BFBFBF;">

7. 您可以选择 **配置管理-应用配置**，查看应用的 AppKey，AppSecret，MasterSecret 等信息，注意区分 AppSercet 与 MasterSecret。具体请参考 [配置管理](https://open.oppomobile.com/new/developmentDoc/info?id=11251)。

    <img alt="oppo 应用信息.png" src="https://yx-web-nosdn.netease.im/common/7ad36a923d2371e9cfc63cc74422ea1a/oppo应用信息.png" style="width:60%;border: 0px solid #BFBFBF;">

## 第二步：在网易云信控制台添加 OPPO 推送证书

1. 在 [网易云信控制台](https://id.grow.163.com/register?h=media&t=media&from=bdpcpz34%7Chttps%3A%2F%2Fdoc.yunxin.163.com%2Fmessaging%2Fsdk-download&clueFrom=nim&referrer=https%3A%2F%2Fapp.yunxin.163.com) 首页的 **应用管理** 中选择应用进入 **应用配置** 页面，单击 **证书管理** 页签。

2. 在 **Android 推送证书** 下单击 **添加证书**，选择证书类型为 **OPPO**，配置 OPPO 推送相关信息。

    <img alt="OPPO 推送.png" src="https://yx-web-nosdn.netease.im/common/2fea0b3b9670077bbb2adc4b6d6baafa/OPPO推送.png" style="width:60%;border: 0px solid #BFBFBF;">

    <table>
        <thead>
            <tr> <th>网易云信推送证书字段</th><th>对应 OPPO 应用的字段信息</th></tr></thead>
                <tr> <td> 证书名称</td><td>用户自定义推送证书名称，最大 32 字符。</br>对应初始化 NIM SDK 时需传入的推送证书信息中的 oppoCertificateName。</td></tr>
                <tr> <td> 应用包名</td><td>对应 OPPO 应用的 <strong>应用包名</strong>，最大 1000 字符。</td></tr>
                <tr> <td> Appkey</td><td>对应 OPPO 应用的 <strong>AppKey</strong>，最大 100 字符。</td></tr>
                <tr> <td> MasterSecret</td><td>对应 OPPO 应用的 <strong>MasterSecret</strong>，最大 1000 字符。</td></tr>
    </table>

3. 根据界面提示，在该对话框内配置证书类型和证书名称等信息。

## 第三步：导入 OPPO 推送 SDK

将 OPPO 推送 SDK 添加到您的 Android 项目。

NIM SDK 当前兼容的 OPPO 推送版本请参考 [更新日志](https://doc.yunxin.163.com/messaging/concept/DM1MjI5MTE?platform=client) 中的 **第三方推送兼容版本**。

1. 下载 OPPO 推送最新的 aar 文件。

2. 在项目的根目录下的 bulid.gradle 中，添加 maven 仓库。

    ```Groovy
    repositories {
        google()
        mavenCentral()
    }
    ```

2. 在 app/build.gradle 文件的 dependencies 块中添加 aar 的依赖。

    ```Groovy
    implementation(name: 'com.heytap.msp_x.x.x', ext: 'aar')
    //以下依赖都需要添加
    implementation 'com.google.code.gson:gson:2.10.1'
    implementation 'commons-codec:commons-codec:1.6'
    implementation 'androidx.annotation:annotation:1.1.0'
    ```

3. 在 bulid 文件中添加 aar 配置。

    ```Groovy
    Android{
    ....

    repositories {
        flatDir {
            dirs 'libs'
        }
    }

    ....
    }
    ```

## 第四步：AndroidManifest.xml 配置

在 app/src/main 目录中，打开 AndroidManifest.xml 文件，添加对应权限。

```XML
<!-- OPPO 推送配置权限 -->
<uses-permission android:name="com.coloros.mcs.permission.RECIEVE_MCS_MESSAGE"/>
<uses-permission android:name="com.heytap.mcs.permission.RECIEVE_MCS_MESSAGE"/>

<!-- OPPO 推送配置项 需要配置以下两项 -->
<!-- 兼容 Q 以下版本 -->
<service
    android:exported="true"
    android:name="com.netease.nimlib.mixpush.oppo.OppoPushService"
    android:permission="com.coloros.mcs.permission.SEND_MCS_MESSAGE">
    <intent-filter>
        <action android:name="com.coloros.mcs.action.RECEIVE_MCS_MESSAGE"/>
    </intent-filter>
</service>

<!-- 兼容 Q 版本 -->
<service
    android:exported="true"
    android:name="com.netease.nimlib.mixpush.oppo.OppoAppPushService"
    android:permission="com.heytap.mcs.permission.SEND_PUSH_MESSAGE">
    <intent-filter>
        <action android:name="com.heytap.mcs.action.RECEIVE_MCS_MESSAGE"/>
        <action android:name="com.heytap.msp.push.RECEIVE_MCS_MESSAGE"/>
    </intent-filter>
</service>
```

## 第五步：防止代码混淆

如果您的应用使用了代码混淆，在 proguard-rules.pro 配置文件中添加以下配置以防止 OPPO SDK 的代码被混淆：

```Groovy
-keep public class * extends android.app.Service
-keep class com.heytap.msp.** { *;}
```

## 推送兼容性

若您的自身业务体系，也需要接入 OPPO 推送，则需要考虑自身业务体系的 OPPO 推送与网易云信消息的 OPPO 推送兼容。

兼容需要完成以下两个步骤：

1. 新建广播接收器

    对于 OPPO 推送，为了接收推送消息，OPPO PUSH SDK 要求您自定义一个继承自 `PushService` 和 `AppPushService` 的 Service，并注册到 AndroidManifest.xml。由于 OPPO 的特殊处理，同时注册多个继承自 `PushService` 和 `AppPushService` 的 Service 会存在收不到消息的情况，要保证自身业务体系的 OPPO 推送与网易云信消息的 OPPO 推送兼容，您需要新建广播接收器，从继承 `PushService` 和 `AppPushService` 改为继承 `OppoPushMessageService` 和 `OppoAppPushMessageService`。`OppoPushMessageService` 和 `OppoAppPushMessageService` 为网易云信提供，推送消息首先被 NIM SDK 接收，如果是自身体系的推送消息，NIM SDK 会将消息传递给 `OppoPushMessageService` 和 `OppoAppPushMessageService`。

    ```Java
    /**
     * 以下这些方法运行在非 UI 线程中, 与 Oppo 的 PushService 方法一一对应。
     * 当开发者自身也接入 Oppo 推送，则应将继承 PushService 改为继承 OppoPushMessageService，其他不变
     * 例如：自定义一个 DemoOppoPushMessageService 继承 OppoPushMessageService
     */
    public class DemoOppoPushMessageService extends OppoPushMessageService {

        @Nullable
        @Override
        public IBinder onBind(Intent intent) {
            return null;
        }

        /**
        * 普通消息
        * @param context
        * @param appMessage
        */
        public void processMessage(Context context, AppMessage appMessage) {
        }

        /**
        * oppo 官方目前还不支持透传消息
        *
        * @param context
        * @param sptDataMessage
        */
        public void processMessage(Context context, SptDataMessage sptDataMessage) {
        }
    }
    ```

    ```Java
    /**
    * 以下这些方法运行在非 UI 线程中, 与 Oppo 的 PushService 方法一一对应。
    * 当开发者自身也接入 Oppo 推送，则应将继承 AppPushService 改为继承 OppoAppPushMessageService，其他不变
    * 例如：自定义一个 DemoOppoAppPushMessageService 继承 OppoAppPushMessageService
    */
    public class DemoOppoAppPushMessageService extends OppoAppPushMessageService {

        @Nullable
        @Override
        public IBinder onBind(Intent intent) {
            return null;
        }

        /**
        * 普通消息
        * @param context
        * @param appMessage
        */
        public void processMessage(Context context, AppMessage appMessage) {
        }

        /**
        * oppo 官方目前还不支持透传消息
        *
        * @param context
        * @param sptDataMessage
        */
        public void processMessage(Context context, SptDataMessage sptDataMessage) {
        }
    }
    ```

2. 在将服务改为继承 `OppoPushMessageService` 和 `OppoAppPushMessageService` 之后，将该服务在 AndroidManifest。xml 中都按如下配置，您只需将服务名称 `OppoService` 替换成自身的服务名。

    ```XML
    <service
        android:name="xxx.DemoOppoPushMessageService"
        android:permission="com.coloros.mcs.permission.SEND_MCS_MESSAGE">
        <intent-filter>
            <action android:name="com.coloros.mcs.action.RECEIVE_MCS_MESSAGE"/>
        </intent-filter>
    </service>

    <service
        android:name="xxx.DemoOppoAppPushMessageService"
        android:permission="com.heytap.mcs.permission.SEND_PUSH_MESSAGE">
        <intent-filter>
            <action android:name="com.heytap.mcs.action.RECEIVE_MCS_MESSAGE"/>
        </intent-filter>
    </service>
    ```

## OPPO 平台限制

### 消息推送分类

**新分类**

OPPO 推送服务将根据消息的内容，将通知分类为 **通讯与服务** 与 **内容与营销** 两大类别，并固定创建对应通道，根据不同类别消息明确发送的通道、内容、发送量级和提醒方式，具体请参考 [OPUSH 消息分类细则](https://open.oppomobile.com/new/developmentDoc/info?id=13189)。

消息类型 | 说明 | 默认展示方式
---- | ---- | ----
通讯与服务 | <li>用户间的聊天消息、通话等信息。<li>与用户自身息息相关的重要通知提醒，用户对接收此类消息有预期。 | 默认为 **通知栏、锁屏** <br>可升级为 **通知栏、锁屏、横幅、铃声、振动**。 |
内容与营销 | 开发者主动向用户发送的对内容或产品推广的通知。 | 仅下拉通知栏展示。 |

**旧分类**

OPPO 推送服务按通知渠道分为 **公信** 和 **私信** 两大类。

| 类型 | 公信 | 私信 |
| ---- | ---- | ---- |
| 推送内容 | 热点新闻、新品推广、平台公告、社区话题、有奖活动等，多用户普适性的内容。 | 个人订单变化、快递通知、订阅内容更新、评论互动、会员积分变动等，与单个用户信息强相关的内容。 |
| 单用户推送限制（条/日） | <ul><li>新闻类（三级分类为新闻类）：5 条。</li><li>其他应用类型：2 条。 | 不限量
| 推送数量限制 | 所有公信类通道共享推送次数，当日达到次数限制后，所有公信类通道将不能再推送消息，目前单日推送数量为：累计注册用户数 * 2。 | 不限量 |
| 配置方式 | 默认 | 需要在 OPPO PUSH 运营平台上登记该通道，并将通道对应属性设置为 **私信**。<note type=notice>请提前创建私信通道，完成发版、登记并发送邮件申请私信通信权限，具体请参考 [私信通道使用](https://open.oppomobile.com/new/developmentDoc/info?id=13216)。 |

### 配置消息推送类型

为了确保推送能正常提醒用户，需设置推送消息的类型 `channel_id`。

- 您可以直接在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置默认的推送消息类型。

    1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 中选择应用，然后单击 **IM 即时通讯** 下的 **功能配置** 按钮进入功能配置页。

        <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b4c08cb9c2fa97f2bcc99523ffae697a/image.png" style="width:40%">

    2. 在顶部选择 **基础功能** 页签，选择 **第三方厂商消息分类**，并单击 **子功能配置**。

        <img src="https://yx-web-nosdn.netease.im/common/b25fd775fa694e181dcbe5259d03da2b/第三方厂商推送.png" style="zoom:70%;" />

    3. 选择对应的第三方厂商，单击 **编辑**，输入 `channel_id` 后 **保存**。

        <img src="https://yx-web-nosdn.netease.im/common/58ee44b1aaee0452123ba81d1054e07e/OPPO推送类型.png" style="zoom:70%;" />

- 也可以通过配置网易云信 NIM SDK 中消息体的 `pushPayload` 来实现。

    示例代码：

    ```Java
    // oppoField 结构示例
    // "oppoField": {
    //     "channel_id": "" //指定下发的通道 ID
    // }
    pushPayload.put("pushTitle", "Set push title here");
    pushPayload.put("oppoField", oppoField);
    ```

:::note note
- **对于传给 OPPO 推送平台的消息类型优先级**：
    - 您上传的消息体的 `pushPayload` 中有分类（channel_id）字段，则使用 `pushPayload` 中的字段值。
    - 如果消息体的 `pushPayload` 中未传入分类（channel_id）字段，则使用默认的推送消息类型（即在 [网易云信控制台](https://app.yunxin.163.com/global/home) 设置的消息类型）。
    - 如果消息体的 `pushPayload` 中未传入分类（channel_id）字段，也没有在网易云信控制台上配置推送消息类型，则该推送消息不会添加分类字段。
- 目前 OPPO 推送不支持透传消息。
:::

### 限额说明

**应用推送总量限制**

| 推送权限 | 应用要求 | 消息推送量（条/日） |
| ---- | ---- | ---- |
| 正式权限 | 应用已上架 OPPO 软件商店 | <li>通讯与服务（原私信）：不限量<li>内容与营销（原公信）：当累计用户数 < 1W 时，可推送总量为 2W/日；当累计用户数 ≥ 1W 时，可推送总量为 **2 倍的累计用户数/日**
| 测试权限 | 应用未上架 OPPO 软件商店 | <li>通讯与服务（原私信）：不支持申请<li>内容与营销（原公信）：1000 |

**单设备推送条数限制**

| 类型 | 内容与营销（原公信） | 通讯与服务（原私信） |
| ---- | ---- | ---- |
| 单用户推送限制（条/日） | <ul><li>新闻类（三级分类为新闻类）：5 条</li><li>其他应用类型：2 条 | 不限量
| 推送数量限制 | 所有公信类通道共享推送次数，当日达到次数限制后，所有公信类通道将不能再推送消息，目前单日推送数量为：累计注册用户数 * 2 | 不限量

**用户接收数量限制**

通过 OPPO 推送通道下发的消息（包含公私信），单用户接收上限 2000 条/日。