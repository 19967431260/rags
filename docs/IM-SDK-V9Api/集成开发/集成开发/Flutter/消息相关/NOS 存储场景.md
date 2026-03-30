

NIM SDK 支持设置 IM 数据在网易对象存储（Netease Object Storage，NOS）服务上的“存储场景”。这里的“存储场景”指需要存储到 NOS 的 IM 数据类型，默认包括多媒体消息的附件资源和用户、群组的资料，且这两类 IM 数据在 NOS 的存储默认不过期。NIM SDK 也支持指定 IM 数据在 NOS 上的过期时间，过期后，数据将被 NOS 删除。



::: note note
多媒体消息附件的存储场景，**推荐使用默认设置**，即“将附件存储到 NOS 且存储永不过期”。
:::


## 前提条件

已完成 [SDK 初始化](https://doc.yunxin.163.com/messaging/docs/DQwNDE4MDM?platform=flutter#步骤2初始化)。



## 实现方法

### 预设存储场景

初始化 SDK 时，可通过`NIMSDKOptions`类下的[`nosSceneConfig`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NIMSDKOptions/nosSceneConfig.html)预设多媒体资源在 NOS 上的存储场景。 


存储场景由`NimNosSceneKeyConstant`定义，主要参数如下：

参数 | 说明
:---|:---
`NIM_DEFAULT_IM` | 将单聊、群聊、聊天室发送的图片、语音、视频和文件消息的附件资源上传至 NOS 进行存储，默认存储永不过期（`NEVER_EXPIRE`），也可通过`updateDefaultIMSceneExpireTime`设置存储过期时间（见如下示例代码），
`NIM_DEFAULT_PROFILE` | 将用户和群组的资料（如头像）等上传至 NOS 进行存，默认存储永不过期（`NEVER_EXPIRE`），也可通过`updateDefaultProfileSceneExpireTime`设置存储过期时间（见如下示例代码）


```dart

static SDKOptions getSDKOptions(Context context) {
        SDKOptions options = new SDKOptions();
         //其他配置
        options.mNosTokenSceneConfig = createNosTokenScene();
        return options;
}

public static final String TEST_NOS_SCENE_KEY="test_nos_scene_key";

private static NosTokenSceneConfig createNosTokenScene() {
      NosTokenSceneConfig nosTokenSceneConfig = new NosTokenSceneConfig();

      //更新默认场景（NimNosSceneKeyConstant.NIM_DEFAULT_IM）对应的过期时间(天)
      nosTokenSceneConfig.updateDefaultIMSceneExpireTime(1);

      //更新默认场景 (NimNosSceneKeyConstant.NIM_DEFAULT_PROFILE) 对应的过期时间(天)
      nosTokenSceneConfig.updateDefaultProfileSceneExpireTime(2);

      //设置自定义场景及对应的过期时间(天)，0代表永不过期。
      //建议sceneKey常量化，这样使用的时候比较方便，目前支持自定义最多10种场景
      nosTokenSceneConfig.appendCustomScene(TEST_NOS_SCENE_KEY, 4);
      return nosTokenSceneConfig;
}
```


### 发消息时设置


构建多媒体消息时，可通过`nosTokenSceneKey`参数设置多媒体资源在 NOS 上的存储场景，默认为`NimNosSceneKeyConstant#NIM_DEFAULT_IM`，即将单聊、群聊和聊天室发送的多媒体资源上传至 NOS 进行存储，且默认存储永不过期。

<div style="width:100px">多媒体消息类型</div> | 构建方法| 相关文档
---- | -------------- 
图片消息| [`createImageMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createImageMessage.html)|[多媒体消息收发](https://doc.yunxin.163.com/messaging/docs/zI0NTgwNDY?platform=flutter#收发多媒体消息)
语音消息 | [`createAudioMesssage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createAudioMessage.html)|^^ 
视频消息 | [`createVideoMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createVideoMessage.html) | ^^
文件消息 | [`createFileMessage`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/MessageBuilder/createFileMessage.html)|^^


## 常见错误码




错误码 | 说明
:---- | :-------------- 
`5` | 使用了不存在的场景，导致资源上传失败。
`4`  | 文件过期后下载文件，导致下载失败。
  