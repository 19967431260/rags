网易云信 IM 即时通讯支持安卓推送平台。本节主要描述安卓推送流程以及推送失败后的排查方法。

## <span id="概念">概念</span>

| **名词** | **解释** |
| ---- | ---- |
| 厂家渠道 | 由华为，小米，魅族，vivo，oppo 等厂家提供的与设备之间的长连接，用于接收推送广播，产生通知栏。 |
| 证书 | 本质上是厂家后台提供的推送参数。 |
| <div style="width: 60pt" >推送 Token </div> | - 推送 Token 是一个总称，是安卓设备上特定 app 的推送唯一 ID，厂家推送服务器收到请求之后，会推送至相应的安卓设备，并展示设备上相应应用的通知栏。 | \
| | - 不同的厂家对 Token 的称呼不同，如小米叫 regid，华为叫 Token 等。 |

## <span id="推送流程">推送流程</span>

<img alt="安卓推送流程图.png" src="https://yx-web-nosdn.netease.im/common/bd65dc99a8f6141438870126ac477db9/安卓推送流程图.png" style="width:100%;border: 1px solid #BFBFBF;">

## <span id="问题排查">问题排查</span>


对应推送流程图，您可以按照本章节介绍的步骤进行排查。

::: note notice
在排查问题前，请确认您已经参照 [实现离线推送](https://doc.yunxin.163.com/messaging/guide/zc1OTI2MTM?platform=android) 集成了推送功能。
:::

### **步骤 1：检查项目推送 Token 是否生成**

1. 获取 SDK 日志。如何获取，请参考《FAQ》[互动白板 SDK 在什么路径提取日志](https://faq.yunxin.163.com/kb/main/#/item/KB0179/1)。
2. 过滤日志中的 `mix_push` 字段。

    - 注册成功的日志。

        <img alt="过滤 1.png" src="https://yx-web-nosdn.netease.im/common/c776492e8b953b4ecceb53a4d44ae9e4/过滤1.png" style="width:100%;border: 1px solid #BFBFBF;">

        <img alt="过滤 2.png" src="https://yx-web-nosdn.netease.im/common/7047b0caea1552d49196ec4d06f97bcc/过滤2.png" style="width:100%;border: 1px solid #BFBFBF;">

    - 注册失败的日志，注册失败无法获取 Token。一般打印的信息都是厂家推送 SDK 回调的，需要根据日志打印的信息在互联网上定位一下原因。

        <img alt="注册失败.png" src="https://yx-web-nosdn.netease.im/common/243329ea12d69d0ef1db6a0fdfad8e60/注册失败.png" style="width:100%;border: 1px solid #BFBFBF;">

    一般情况下，token 生成之后，只要 IM 登录是成功的，那么 Token 一定就正常上报到网易云信。

### **步骤 2：检查是否满足推送条件**

具体触发消息推送的条件，请参考《FAQ》[关于消息推送](https://faq.yunxin.163.com/kb/main/#/item/KB0065/1-1)。

### **步骤 3：检查手机的通知栏权限是否开启置**

安卓 8.0 开始加入推送 channel 的概念，所以建议在测试的时候将所有推送的 channel 都打开。

<img alt="安卓缩放.png" src="https://yx-web-nosdn.netease.im/common/4e8a4e7aeaa659d3d711458b700baf6c/安卓缩放.png" style="width:20%;border: 1px solid #BFBFBF;">

### **步骤 4：提交分析**

如果 Token 已经正常生成，并且满足推送条件，但是设备依旧收不到推送通知栏，可以将 Token，SDK 日志，证书名称等信息 [提交工单](https://app.yunxin.163.com/global/service/ticket/create) 联系网易云信技术支持工程师。

## <span id="关于单击通知栏">关于单击通知栏</span>

- 参考 [开发文档](https://doc.yunxin.163.com/messaging/guide/zc1OTI2MTM?platform=android#%E6%8E%A8%E9%80%81%E9%80%9A%E7%9F%A5%E6%A0%8F%E8%B7%B3%E8%BD%AC) 的说明
- 华为自定义单击跳转。

    华为推送提供一个 click_action 的字段，可以用于自定义通知栏跳转。具体请参考华为的 [开发文档](https://developer.huawei.com/consumer/cn/doc/development/HMS-References/push-sendapi#clickaction)。

    这里的 `intent` 内容可以在应用的 `launch activity` 的 `getIntent` 方法中获取到。下图中的 `notification` 内容在实际发消息时，传在 `payload` 的"hwField"内即可。

    <img alt="华为回调.png" src="https://yx-web-nosdn.netease.im/common/4dd2462958b529b65e7f33501ba1cb21/华为回调.png" style="width:100%;border: 1px solid #BFBFBF;">

## <span id="关于通知类型">关于通知类型</span>

有部分厂家会区分营销类通知和消息通知，可以考虑通过以下方式配置：

```JSON
{
    // vivo 推送 可以自定义 https://dev.vivo.com.cn/documentCenter/doc/362#w2-98542835 里的传参
    "vivoField":{
        "classification":1, // 指定为系统消息
        "category":"IM" // 二级分类
    },
    // oppo 推送 7.8.0 开始支持。可以自定义 https://open.oppomobile.com/wiki/doc#id=10688 中的参数
    "oppoField":{
        // 指定通道
        "channel_id":"1233"
    }
    // 华为推送，可以自定义 https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/https-send-api-0000001050986197#section13271045101216 中的参数，目前支持的是其中 AndroidNotification 结构体
    "hwField":{
        "title":"friend",
        "body":"heolo"
    }
    // 注意：小米的没有对应的 Field，各参数直接放在 payload 的第一级的键值对中
    // 小米的通道 可以自定义 https://dev.mi.com/console/doc/detail?pId=1163#_0 中 extra 下的各个属性。
    "channel_id":"123345",
    // 可选项，指定在特定的网络环境下才能接收到消息。目前仅支持指定"wifi"。
    "connpt":"wifi"
}
```

更多示例请参考 [推送 payload 配置](https://doc.yunxin.163.com/messaging/guide/DQyNjc5NjE?platform=server)。

## <span id="厂商通道限流">厂商通道限流</span>

**1. 小米通道**

请访问 [小米文档](https://dev.mi.com/console/doc/detail?pId=2086)。

- 限制点：普通级别消息（默认），每天会限流。
- 解决：客户自行申请重要级别消息 并申请 channel，在发消息时，setPushPayload 中传{"channel_id":"12345"}。

**2. 华为通道**

请访问 [华为文档](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-Guides/faq-0000001050042183#section196822541234)。

- 限制点：每天向某个设备上某个应用发送消息的数量不超过 3000 条，超过 3000 条会进行限流。
- 解决：无法解决，华为不支持申请不限流以及增量，3000 条常规够用。

**3. oppo 通道**

请访问 [oppo 文档](https://open.oppomobile.com/wiki/doc#id=10743)。

- 限制点：公信通道（默认）可推送数量，每日推送总量有上限。
- 解决：客户自行申请私信通道，并申请 channel，在发消息时，`setPushPayload` 中传{ "oppoField":{"channel_id":"12345"}}。

**4. vivo 通道**

请访问 [vivo 文档](https://dev.vivo.com.cn/documentCenter/doc/359#w2-98542835)。

- 限制点：运营消息（默认），单用户单应用每天收到的消息条数上限为 5 条。
- 解决：在发消息时，`setPushPayload` 中传{ "vivoField":{"classification":1}}，指定为系统消息。

:::note note
如果系统消息量级不够用，需要向 vivo 申请增量。
:::

## <span id="SDK通道Channel">SDK 通道 Channel</span>

部分客户想直接使用 SDK 中注册的 channel，作为厂商(小米、oppo)的申请 channel。

SDK 中 channel 信息：

- 默认，有声音和震动

    ```Java
    // default channel
    private static final String NIM_CHANNEL_ID = "nim_message_channel_001";
    private static String NIM_CHANNEL_NAME = "Instant messages channel";
    private static String NIM_CHANNEL_DESC = "Instant messages notification";
    ```
- 免打扰，无声音无振动
    ```Java
    // no disturbing channel
    private static final String NIM_NO_DISTURBING_CHANNEL_ID = "nim_message_channel_002";
    private static String NIM_NO_DISTURBING_CHANNEL_NAME = "No disturbing instant messages channel";
    private static String NIM_NO_DISTURBING_CHANNEL_DESC = "No disturbing instant messages notification";
    ```
- 有声音无振动
    ```Java
    // just ring
    private static final String NIM_JUST_RING_CHANNEL_ID = "nim_message_channel_003";
    private static String NIM_JUST_RING_CHANNEL_NAME = "Just ring channel";
    private static String NIM_JUST_RING_CHANNEL_DESC = "Just ring instant messages notification";
    ```
- 无声音有振动
    ```Java
    // just vibrate
    private static final String NIM_JUST_VIBRATE_CHANNEL_ID = "nim_message_channel_004";
    private static String NIM_JUST_VIBRATE_CHANNEL_NAME = "Just vibrate channel";
    private static String NIM_JUST_VIBRATE_CHANNEL_DESC = "Just vibrate instant messages notification";
    ```

## <span id="厂商通道错误码文档">厂商通道错误码文档</span>

| **厂家** | **错误码** |
| ---- | ---- |
| 小米 | [客户端错误码](https://dev.mi.com/console/doc/detail?pId=41#_2_1)、[服务端错误码](https://dev.mi.com/console/doc/detail?pId=1557) |
| 华为 | [客户端错误码](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/error-code-0000001050255690)、[服务端错误码](https://developer.huawei.com/consumer/cn/doc/development/HMSCore-References/https-send-api-0000001050986197#section13968115715131) |
| oppo | [客户端错误码](https://open.oppomobile.com/new/developmentDoc/info?id=11224)、[服务端错误码 API](https://open.oppomobile.com/new/developmentDoc/info?id=11235)，见 ReturnCode.ErrorCode |
| vivo | [客户端和服务端错误码](https://dev.vivo.com.cn/documentCenter/doc/368) |
| 魅族 | [客户端错误码](http://open.res.flyme.cn/fileserver/upload/file/202109/7bf101e2843642709c7a11f4b57861cd.pdf)、[服务端错误码](http://open.res.flyme.cn/fileserver/upload/file/202111/f6e1173e5d834d2692b06529ca1a493c.pdf) |
| 荣耀 | [客户端错误码](https://developer.hihonor.com/cn/kitdoc?category=%E5%9F%BA%E7%A1%80%E6%9C%8D%E5%8A%A1&kitId=11002&navigation=guides&docId=sdk-error-code.md&source=Search_DoccenterSearchResults)
| FCM | [错误码](https://firebase.google.cn/docs/reference/fcm/rest/v1/ErrorCode?hl=zh-cn)

## 常见问题

### 我如何知道我使用的 IM SDK 该配套使用平台厂商的推送渠道哪个版本的 SDK？

请参考 [实现离线推送](https://doc.yunxin.163.com/messaging/guide/zc1OTI2MTM?platform=android#%E5%AE%9E%E7%8E%B0%E6%B5%81%E7%A8%8B) 查看 SDK 之间的兼容情况。