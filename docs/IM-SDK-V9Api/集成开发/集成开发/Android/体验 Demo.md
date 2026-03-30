<!--keywords: 示例项目,demo, Demo , demo 源码, Demo 源码,示例 GitHub 项目源码 -->

网易云信为您提供即时通讯 Demo 应用（包括 IM Demo 和圈组 Demo）。您可以安装 Demo，快速了解和体验即时通讯服务的多项能力，如会话、会话列表、通讯录和 [圈组](https://doc.yunxin.163.com/messaging/concept/jUyODc1NDM)。网易云信也提供网易云信派对 Demo，方便您直观感受基于 IM 能力可以实现的多种娱乐社交业务场景。

## 下载 Demo

扫描以下二维码下载并体验示例项目。

<style>
.container {
  display: flex;
  justify-content: space-between;
}

.column {
  flex: 1;
  margin: 5px;
  text-align: center;
}

.column img {
  width: 100%;
  height: auto;
}
</style>

<div class="container">
  <div class="column">
    <figure>      <a href="https://demo-app.yunxin.163.com/aim"><img alt="im-android.png" src="https://yx-web-nosdn.netease.im/common/e093fd33c08db9ef2bd5d9764725effb/image.png" style="width:50%;border: 1px solid #BFBFBF;"></a><figcaption style="width: 100%; text-align: center; caption-side: top;"><b>IM Demo</b></figcaption><span>包含单聊、群聊、通讯录等模块的示例项目</span> </figure>
  </div>
  <div class="column">
    <figure>      <a href="https://demo-app.yunxin.163.com/aqchat"><img alt="qchat-android.png" src="https://yx-web-nosdn.netease.im/common/47fd90a252402479eb34e097d466af60/image.png" style="width:50%;border: 1px solid #BFBFBF;"></a><figcaption style="width: 100%; text-align: center; caption-side: top;"><b>圈组 Demo</b></figcaption><span>体验类 <b>Discord</b> 场景的频道类型示例项目</span> </figure>
  </div>
  <div class="column">
    <figure>
    <a href="https://demo-app.yunxin.163.com/aparty"><img alt="party-android.png" src="https://yx-web-nosdn.netease.im/common/3d41c59074cde247db379560a382223f/image.png" style="width:50%;border: 1px solid #BFBFBF;"></a><figcaption style="width: 100%; text-align: center; caption-side: top;"><b>云信派对 Demo</b></figcaption><span>包含 1 对 1 娱乐社交、语聊房和一起听业务场景</span>
</figure>
  </div>
</div>

::: note note
以上 Demo 的设备运行环境要求 Android v7.0 以及以上版本。
:::

## 效果展示

### IM Demo

- **消息模块主要界面**

    <img alt="消息模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/fc262d70946ca08200288594a38ec4fd/消息模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

- **群聊模块主要界面**

    <img alt="群聊模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/3d702b13a5a198d7f5febfb748b47191/群聊模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

- **通讯录模块主要界面**

    <img alt="通讯模块主要界面.png" src="https://yx-web-nosdn.netease.im/common/bc1c7f3030ccf1f2b42752e54bd27f2e/通讯模块主要界面.png" style="width:80%;border: 1px solid #BFBFBF;">

### 圈组 Demo

<img src="https://yx-web-nosdn.netease.im/common/0936186bd07b5e75f8173cbab4e2742c/圈组Demo效果.png" />

<img src="https://yx-web-nosdn.netease.im/common/903e4b912aae8d39e42ccc693fbb0e95/身份组的Demo效果.png" />

### 云信派对

- **1 对 1 娱乐社交**

    通过网易云信派对提供的 1 对 1 娱乐社交场景模块，您可以体验音视频呼叫、美颜、安全通、高接通等多种能力。1 对 1 娱乐社交场景模块的界面效果如下图所示。

    <img alt="1v1.png" src="https://yx-web-nosdn.netease.im/common/04d5dfec3f1da41b40a6578c2a16ee52/1v1.png" style="width:80%;border: 1px solid #BFBFBF;">

    快速集成的方法请参考《1 对 1 娱乐社交场景方案》<a href="https://doc.yunxin.163.com/1v1-social/guide/TM5NDk4NDI?platform=android" target="_blank">实现 1 对 1 音视频通话</a>。

    单击查看 [1 对 1 娱乐社交示例 GitHub 项目源码](https://github.com/netease-kit/1V1)。

- **语聊房**

    通过网易云信派对提供的语聊房场景模块，您可以体验多人语音聊天、麦位管理、给指定的麦上用户送礼物，拥有极致音质、防炸麦、AI 降噪处理能力。语聊房场景模块的界面效果如下图所示。

    <img alt="语聊房.png" src="https://yx-web-nosdn.netease.im/common/f8808eed38d0e20827cd4101f7643d98/语聊房.png" style="width:80%;border: 1px solid #BFBFBF;">

    快速集成的方法请参考《语聊房场景方案》<a href="https://doc.yunxin.163.com/group-voice-room/guide?platform=android" target="_blank">实现语聊房（基于 NERoom）</a>。

    单击查看 [语聊房示例 GitHub 项目源码](https://github.com/netease-kit/NEChatroom)。

- **一起听**

    通过云信派对提供的一起听场景模块，您可以体验双人私密房场景，边听音乐边聊天。一起听场景模块的界面效果如下图所示。

    <img alt="一起听.png" src="https://yx-web-nosdn.netease.im/common/54245b581b376a17bfd44591aac77215/一起听.png" style="width:80%;border: 1px solid #BFBFBF;">

    快速集成的方法请参考《语聊房场景方案》<a href="https://doc.yunxin.163.com/group-voice-room/guide/TI0MzEyMzQ?platform=android" target="_blank">实现一起听（基于 NERoom）</a>。

    单击查看 [一起听示例 GitHub 项目源码](https://github.com/netease-kit/NEChatroom/tree/voiceroomkit)。