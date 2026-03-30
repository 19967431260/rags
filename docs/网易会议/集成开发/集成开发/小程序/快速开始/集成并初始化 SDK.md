本文为您展示通过 NEMeetingKit 实现音视频会议的相关步骤，帮助您在业务中实现创建会议、预约会议、查询会议信息等在线会议场景下的相关能力。

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案。具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

微信小程序相关操作：

1. 注册微信小程序账号，并通过企业认证，并在 <a href="https://mp.weixin.qq.com/" target="_blank"> **微信公众平台** </a> > **开发** > **开发管理** > **接口设置** 中打开实时播放音视频流和实时录制音视频流的开关，以自助开通该组件权限。

    <img alt="authority.jpg" src="https://yx-web-nosdn.netease.im/common/177707d81729a491d9d10cdf82c66aca/authority.jpg" style="width:80%;border: 1px solid #BFBFBF;">

    ::: note note
    出于政策和合规的考虑，微信暂未放开所有小程序对实时音视频功能（即 <a href="https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-pusher.html" target="_blank">live-pusher</a> 和 <a href="https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-player.html" target="_blank">live-player</a> 标签）的支持，仅 <a href="https://developers.weixin.qq.com/miniprogram/dev/component/live-pusher.html" target="_blank">指定类目</a> 的应用可以开通小程序推拉流标签。
    :::

2. 在微信小程序中创建微信的 <a href="https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-pusher.html" target="_blank">live-pusher</a> 组件和 <a href="https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-player.html" target="_blank">live-player</a> 组件，分别实现音视频播放和音视频录制功能。

3. 部署安装微信的移动端设备以供调试和运行体验。

## 开发环境

在客户端实现音视频会议功能之前，请您准备以下开发环境：

| 名称 | 具体要求 |
| ---- | ---- |
| Android 端的微信 App | 7.0.8 及以上版本 |
| iOS 端的微信 App | 7.0.9 及以上版本 |
| 小程序基础库 | 2.10.0 及以上版本 |
| <a href="https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html" target="_blank">微信开发者工具</a> | 最新版本 |

::: note note
- 由于微信开发者工具不支持原生组件（即 <[live-pusher](https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-pusher.html) 和 <[live-player](https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-player.html)> 标签），需要在真机上进行运行体验。
- 由于小程序测试号不具备 <[live-pusher](https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-pusher.html) 和 <[live-player](https://mp.weixin.qq.com/debug/wxadoc/dev/component/live-player.html)> 的使用权限，需要申请常规小程序账号进行开发。
- 暂不支持 uni-app 开发环境，请使用原生小程序开发环境。
:::

## <span id="配置白名单并打开端口">配置白名单并打开端口</span>

如果您的网络环境部署了防火墙，请在 <a href="https://mp.weixin.qq.com/" target="_blank"> **微信公众平台** </a> > **开发** > **开发管理** > **开发设置** 中将以下域名及对应端口添加到域名白名单中。

<img alt="配置白名单.png" src="https://yx-web-nosdn.netease.im/common/9a6216ce0df8622bc63d67c895930470/配置白名单.png" style="width:80%;border: 1px solid #BFBFBF;">

**域名：**

```Bash
# http 接口
https://statistic.live.126.net
https://lbs.netease.im
https://nrtc.netease.im
https://wlnimsc0.netease.im
https://wlnimsc1.netease.im
https://roomkit.netease.im
# websocket 接口
wss://webrtcgwcn.netease.im
wss://webrtcgwhz.netease.im
```

**端口：**

<table border=1>
    <tr>
        <th width=20%><b>目标端口</b></th>
        <th width=10%><b>协议</b></th>
        <th width=10%><b>操作</b></th>
    </tr>
    <tr>
        <td>80、443
        </td>
        <td>TCP
        </td>
        <td>允许
        </td>
    </tr>
    <tr>
        <td>30000 ~ 40000
        </td>
        <td>UDP
        </td>
        <td>允许
        </td>
    </tr>
</table>

## 集成 SDK

1. 引入 NEMeetingKit 和 NEChatRoomUI 两个文件夹 至 `components` 文件。

2. 在使用网易会议组件的 page 中引入组件。

    由于手机屏幕限制，需要配置屏幕旋转参数为横屏，示例代码如下。
    ```
    // xxx.json
    {
        "pageOrientation": "landscape", // 设置为横屏
        "usingComponents": {
            "NEMeetingKit": "../../components/NEMeetingKit/NEMeetingKit" // 组件所在路径
        }
    }
    ```

3. 使用组件。

    ```XML
    // xxx.wxml
    <NEMeetingKit
        id="meeting-component"
        bindmeetingClosed="onMeetingClosed"
        binddisconnect="onDisconnect"
        bindkicked="onKicked"
        bindleave="leaveRoom"
        bindonLoginStateChange="onLoginStateChange">
    </NEMeetingKit>
    ```

## <span id="初始化 SDK">初始化 SDK</span>

### 调用时机

在调用 SDK 其他接口之前，您首先需要完成初始化操作。

### 注意事项

- 初始化是一个异步操作，您需要确保异步回调成功之后，再进行调用 API。
- 应用名称会显示在会议界面的顶部标题栏中。若不额外设置应用名称，则标题默认显示为 **会议**。

### 调用步骤

调用 `initSDK` 方法初始化会议小程序组件。

::: note notice
请不要重复初始化，否则 SDK 会报错。
:::

**示例代码**如下：
```
// 通过小程序提供的 this.selectComponent() 方法获取组件实例
this.meetingComponent = this.selectComponent('#meeting-component')

/**
  * 初始化
  * @param param
  * @param param.debug 是否开启调试模式
  * @param param.appKey appKey
  * @param param.baseDomain [可选] 发起请求的domain，若未填则默认为https://roomkit.yunxinapi.com
  * @param param.offChatRoom [可选] 关闭聊天室功能，默认开启
  * @param param.defaultDirectionalTags [可选] 聊天室定向发送消息的标签组
  * @param param.enableOrientChat [可选] 是否开启聊天室定向发送消息模式，默认关闭
  * @param param.isHideMute [可选] 小程序最小化后是否需要后台关闭音视频，默认开启
  * @param param.enableRealtimeLog [可选] 是否开启实时日志上报（微信公众号后台查看），默认开启
  * @param param.imPrivateConf [可选] IM SDK私有化配置，仅限于私有化配置时使用
  * @param param.neRtcServerAddresses [可选] G2 SDK私有化配置，仅限于私有化配置时使用
  */
this.meetingComponent.initSDK({
  debug,
  appKey,
  baseDomain,
  defaultDirectionalTags,
  enableOrientChat,
  isHideMute,
  enableRealtimeLog,
  imPrivateConf,
  neRtcServerAddresses
})
```

## <span id="销毁 SDK">销毁 SDK</span>

调用 `destroy` 方法销毁会议 MiniApp 组件，退出会议。

**示例代码**如下：

```
this.meetingComponent.destroy()
```