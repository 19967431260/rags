网易云信 IM 即时通讯 NIM SDK 自 6.3.0 之后的版本新增支持 vivo 推送。本文主要介绍如何集成 vivo 厂商的离线推送通道，使消息通过 vivo 推送服务离线推送至未在线的用户。

## 第一步：启用推送服务

**若已在 vivo 开放平台创建应用，则忽略该步骤。更多 vivo 推送服务的信息请参考 [vivo 推送接入流程](https://dev.vivo.com.cn/documentCenter/doc/281)。**

1. 在 [vivo 开放平台](https://dev.vivo.com.cn/) 注册开发者账号并完成认证，具体请参考 [企业开发者注册](https://dev.vivo.com.cn/documentCenter/doc/2)。

2. 登录 [vivo 开放平台](https://dev.vivo.com.cn/)，单击 **应用管理**，选择 **应用** 并单击 **创建应用**。

    <img alt="vivo 管理中心.png" src="https://yx-web-nosdn.netease.im/common/462beda7b50ea97e9c948836640e9785/vivo管理中心.png" style="width:60%;border: 0px solid #BFBFBF;">

    <img alt="vivo 创建应用.png" src="https://yx-web-nosdn.netease.im/common/892f81869bcddc9e086da996f1815a95/vivo创建应用.png" style="width:60%;border: 0px solid #BFBFBF;">

3. 填写应用包名、应用名称、上传应用 ICON，然后单击 **创建** 完成应用的创建。

    <img alt="vivo 创建应用详情.png" src="https://yx-web-nosdn.netease.im/common/6722ef08e5c2dabea21c0659a67d5676/vivo创建应用详情.png" style="width:60%;border: 0px solid #BFBFBF;">

4. 上传 APK 包，完善其他信息后，单击 **提交**，等待审核。审核通过上架后，在 vivo 应用商店中可查看。

5. 进入 [vivo 推送服务](https://dev.vivo.com.cn/promote/pushNews)，单击 **立即接入**。

    <img alt="vivo 接入.png" src="https://yx-web-nosdn.netease.im/common/dbe7333404bfecb449791cf2db2f1a00/vivo接入.png" style="width:60%;border: 0px solid #BFBFBF;">

6. 单击 **推送申请**，在申请页面选择软件包类型，目标应用等信息后，提交申请。

    <img alt="vivo 申请推送.png" src="https://yx-web-nosdn.netease.im/common/92d81794c5762eb7bd688a2b4e99d48d/vivo申请推送.png" style="width:60%;border: 0px solid #BFBFBF;">

    <img alt="vivo 申请应用详情.png" src="https://yx-web-nosdn.netease.im/common/a443f386d8c20fb5a66768c0d5fa0464/vivo申请应用详情.png" style="width:60%;border: 0px solid #BFBFBF;">

7. 提交后，请关注开放平台应用的上架状态，您可在申请页面查看审核结果。

8. 应用上架后，选择左侧导航栏的 **应用信息**，查看应用的 AppID、AppKey、AppSecret 等信息。

    <img alt="vivo 应用详情.png" src="https://yx-web-nosdn.netease.im/common/207b4bfbd9f7d1291570693fbbca1362/vivo应用详情.png" style="width:60%;border: 0px solid #BFBFBF;">

## 第二步：添加 vivo 推送证书

1. 在 [网易云信控制台](https://id.grow.163.com/register?h=media&t=media&from=bdpcpz34%7Chttps%3A%2F%2Fdoc.yunxin.163.com%2Fmessaging%2Fsdk-download&clueFrom=nim&referrer=https%3A%2F%2Fapp.yunxin.163.com) 首页的 **应用管理** 中选择应用进入 **应用配置** 页面，单击 **证书管理** 页签。

2. 在 **Android 推送证书** 下单击 **添加证书**，选择证书类型为 **VIVO**，配置 vivo 推送相关信息。

    <img alt="vivo 推送.png" src="https://yx-web-nosdn.netease.im/common/245f954ee8f2ec1aae745b49fc9e2ddf/vivo推送.png" style="width:60%;border: 0px solid #BFBFBF;">

    <table>
        <thead>
            <tr> <th>网易云信推送证书字段</th><th>对应 vivo 应用的字段信息</th></tr></thead>
                <tr> <td> 证书名称</td><td>用户自定义推送证书名称，最大 32 字符。</br>对应初始化 NIM SDK 时需传入的推送证书信息中的 vivoCertificateName。</td></tr>
                <tr> <td> 应用包名</td><td>对应 vivo 应用的<strong>应用包名</strong>，最大 1000 字符。</td></tr>
                <tr> <td> AppID</td><td>对应 vivo 应用的 <strong>AppID</strong>，最大 1000 字符。</td></tr>
                <tr> <td> AppSecret</td><td>对应 vivo 应用的 <strong>AppSecret</strong>，最大 5000 字符。</td></tr>
                <tr> <td> Appkey</td><td>对应 vivo 应用的 <strong>AppKey</strong>，最大 100 字符。</td></tr>
    </table>

3. 根据界面提示，在该对话框内配置证书类型和证书名称等信息。

    <note type=note>其中的 **证书名称** 即为初始化 SDK 时需传入的推送信息中的 `vivoCertificateName`。</note>

## 第三步：导入 vivo 推送 SDK

将 vivo 推送客户端 SDK 添加到您的 Android 项目。vivo 推送的客户端 SDK 集成，具体可参考 [集成指南](https://dev.vivo.com.cn/documentCenter/doc/365#w2-93531329)。

NIM SDK 当前兼容的 vivo 推送版本请参考 [更新日志](https://doc.yunxin.163.com/messaging2/concept/zI4NDQ1NDk?platform=client) 中的 **第三方推送兼容版本**。

1. 下载 vivo_pushSDK，并将下载的 aar 文件拷贝到您的项目路径的 app/libs 目录。

2. 在项目 app 目录下的 build.gradle 添加 aar 依赖。

    ```Groovy
    //vivo_pushSDK_vx.x.x.x_xxx.aar 仅为举例，请替换为实际的依赖版本
    dependencies {
        implementation fileTree(include: ['*.jar'],   dir: 'libs')
        implementation   files("libs/vivo_pushSDK_vx.x.x.x_xxx.aar")
    }
    ```

## 第四步：AndroidManifest.xml 配置

1. 在 app/src/main 目录中，打开 AndroidManifest.xml 文件，添加对应权限。

    ```XML
    <!-- 配置的 service, activity, receiver -->
    <service
        android:name="com.vivo.push.sdk.service.CommandClientService"
        android:permission="com.push.permission.UPSTAGESERVICE"
        android:exported="true"/>

    <receiver android:name="com.netease.nimlib.mixpush.vivo.VivoPushReceiver">
        <intent-filter>
            <!-- 接收 push 消息 -->
            <action android:name="com.vivo.pushclient.action.RECEIVE"/>
        </intent-filter>
    </receiver>
    ```

2. 在 AndroidManifest.xml 中，添加配置 App ID 与 App Key。

    ```XML
    <meta-data
        android:name="com.vivo.push.api_key"
        android:value="{您的 vivo 推送 app key}"/>
    <meta-data
        android:name="com.vivo.push.app_id"
        android:value="{您的 vivo 推送的 app id}"/>
    ```

## 第五步：防止代码混淆

如果您的应用使用了代码混淆，在 proguard-rules.pro 配置文件中添加以下配置以防止 vivo SDK 的代码被混淆：

```Groovy
-dontwarn com.vivo.push.**
-keep class com.vivo.push.**{*; }
-keep class com.vivo.vms.**{*; }
```

## 推送兼容性

若您的自身业务体系，也需要接入 vivo 推送，则需要考虑自身业务体系的 vivo 推送与网易云信消息的 vivo 推送兼容。

兼容需要完成以下两个步骤：

1. 新建广播接收器。

    对于 vivo 推送，为了接收推送消息，vivo push SDK 要求您自定义一个继承自 `OpenClientPushMessageReceiver` 的 `BroadcastReceiver`，并注册到 AndroidManifest.xml。由于 vivo 的特殊处理，同时注册多个继承自 `OpenClientPushMessageReceiver` 的 `BroadcastReceiver` 会存在收不到消息的情况，要保证自身业务体系的 vivo 推送与网易云信消息的 vivo 推送兼容，您需要新建广播接收器，从继承 `OpenClientPushMessageReceiver` 改为继承 `VivoPushMessageReceiver`。`VivoPushMessageReceiver` 为网易云信提供，推送消息首先被 NIM SDK 接收，如果是自身体系的推送消息，NIM SDK 会将消息传递给 `VivoPushMessageReceiver`。

    ```Java
    /**
    * 以下这些方法运行在非 UI 线程中, 与 vivo SDK 的 OpenClientPushMessageReceiver 方法一一对应。
    * 当开发者自身也接入 vivo 推送，则应将继承 OpenClientPushMessageReceiver 改为继承 VivoPushMessageReceiver，其他不变
    * 例如：自定义一个 DemoVivoPushMessageReceiver 继承 VivoPushMessageReceiver
    */

    public class DemoVivoPushMessageReceiver extends VivoPushMessageReceiver {

        @Override
        public final void onReceive(Context context, Intent intent) {
        }

        public void onNotificationMessageClicked(Context context, UPSNotificationMessage upsNotificationMessage) {
            //该接口仅用于解决 3.0.0.0_480 之前的版本升级 Push SDK 过程中发送的老版本打开自定义通知（skiptype=3）需要依赖单击回调完成跳转时使用，新版本通知单击该单击回调是不可用的。
        }

        public void onReceiveRegId(Context context, String s) {
        }
    }
    ```

2. 配置新广播的名称。

    在将广播接收器改为继承 `VivoPushMessageReceiver` 之后，将该广播在 `AndroidManifest` 中配置如下，开发者只需将广播名称 `VivoPushMessageReceiver` 替换成自身的广播名。此外，请不要为此 `Receiver` 配置 `priority`。

    ```XML
    <receiver android:name="xxx.DemoVivoPushMessageReceiver">
        <intent-filter>
            <action android:name="com.vivo.pushclient.action.RECEIVE" />
        </intent-filter>
    </receiver>
    ```

## vivo 平台限制

### 消息推送类型配置

vivo 的推送消息分为 [运营消息和系统消息](https://dev.vivo.com.cn/documentCenter/doc/359)，需要在推送时进行指定，将默认为运营消息。开发者需根据自身应用的通知场景，将消息内容按照对应消息类别发送。

vivo 推送消息的类型通过 `classification` 来判断。

- 您可以直接在 [网易云信控制台](https://app.yunxin.163.com/global/home) 上配置默认的推送消息类型。

    1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 首页 **应用管理** 中选择应用，然后单击 **IM 即时通讯** 下的 **功能配置** 按钮进入功能配置页。

        <img alt="image.png" src="https://yx-web-nosdn.netease.im/common/b4c08cb9c2fa97f2bcc99523ffae697a/image.png" style="width:40%">

    2. 在顶部选择 **基础功能** 页签，选择 **第三方厂商消息分类**，并单击 **子功能配置**。

        <img src="https://yx-web-nosdn.netease.im/common/b25fd775fa694e181dcbe5259d03da2b/第三方厂商推送.png" style="zoom:70%;" />

    3. 选择对应的第三方厂商，单击 **编辑**，选择类型后 **保存**。

        <img src="https://yx-web-nosdn.netease.im/common/d6b2f0e5038a7a0269bd3d3533e50d0a/vivo推送类型.png" style="zoom:70%;" />

- 也可以通过配置网易云信 NIM SDK 中消息体的 `pushPayload` 来实现。

    在其中添加以 `vivoField` 为 key 的 Map 或者 JSONObject 数据即可，数据格式参照 [vivo 文档](https://dev.vivo.com.cn/documentCenter/doc/363#w2-06798783)。

    示例代码如下：

    ```Java
    int classification = vivoClassificationCheckBox.isChecked() ? 1 : 0;
    Map<String, Object> pushPayload = msg.getPushPayload();
    pushPayload = pushPayload == null ? new HashMap<>() : pushPayload;

    //vivoField
    Map<String, Object> vivoField = new HashMap<>();
    vivoField.put("classification", classification);
    pushPayload.put("vivoField", vivoField);
    ```

    :::note note
    对于传给 vivo 推送平台的消息类型优先级：
    - 您上传的消息体的 `pushPayload` 中有分类（classification）字段，则使用 `pushPayload` 中的字段值。
    - 如果消息体的 `pushPayload` 中未传入分类（classification）字段，则使用默认的推送消息类型（在网易云信控制台设置的消息类型）。
    - 如果消息体的 `pushPayload` 中未传入分类（classification）字段，也没有在网易云信控制台上配置推送消息类型，则该推送消息不会添加分类字段。
    :::

### **推送消息限额**

vivo 推送消息对于不同消息类型有不同的限制，如下表所示，详情请参考 [vivo 推送消息限制说明](https://dev.vivo.com.cn/documentCenter/doc/695)。

<table>
  <thead>
       <tr> <th>消息类型</th><th>推送数量限制</th><th>用户接收数量限制</th></tr></thead>
      <tr> <td> 系统消息 </td><td>通知开启有效用户数*3（可申请消息不限量权限）</td><td>无限制</td></tr>
      <tr> <td> 运营消息 </td><td><ul><li>新闻资讯类：通知开启有效用户数*3</li><li>其他类：通知开启有效用户数*2</li></ul></td><td><ul><li>新闻资讯类：5 条</li><li>其他类：2 条</li></ul></td></tr>
      <tr> <td> 测试消息 </td><td colspan=2><ul><li>审核中的应用，推送权限为 <b>受限</b>，只能通过 API，向在 Web 页面中添加的测试设备发送测试消息，测试设备数量上限为 20 个，测试消息不受量级和频控限制。</li><li>发送测试消息时注意填写 <code>pushMode=1</code>（0：正式推送；1：测试推送；不填默认为 0）。若未填写，当文案相同时，将被当做重复运营消息被去重。</li></ul></td></tr>

</table>

::: note note
- **通知开启的有效用户**：应用集成的 vivo 推送 SDK 订阅成功，且设备近 14 天 内有联网的通知权限开启用户。
- 通知开启有效用户数 < 10000，则运营消息量级默认为 10000。
- 通知开启的有效用户数及可发送运营消息量级，可在推送运营后台查询。
- 推送限额数以 **到达量** 计算，当日到达量超限则计入管控。
:::

### **额度查询**

在 **[vivo 开放平台](https://dev.vivo.com.cn/openAbility/pushNews)** > **推送统计** > **推送数据** 中可以查看 SDK 订阅数和可发送的消息总量，详情请参考 [vivo 推送平台使用指南](https://dev.vivo.com.cn/documentCenter/doc/151#s-6oxmplyb)。

### 推送速度

- 应用推送速度配置策略：vivo 推送 QPS 根据通知开启的有效用户数，默认最低 3000/秒，最高 5000/秒。

    通知开启的有效用户数 | 推送速度
    ---- | ----
    0-500 W | 3000
    500W-800 W | 4000
    800W 以上 | 5000

- 目前接口有调用频率限制。
- vivo 推送系统目前支持 100 万级并发。