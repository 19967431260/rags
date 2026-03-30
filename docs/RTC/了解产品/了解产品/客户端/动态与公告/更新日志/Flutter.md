本文介绍网易云信音视频通话 NERTC SDK Flutter 端的版本更新日志。如需了解更多功能详情，请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=flutter) 和 [查看 API 文档](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/index.html)。

<style>
table th:first-of-type {width: 35%;}
</style>

## 5.9.20 (2026-01-30)

**新增功能**

Android、iOS 支持请求大型语言模型。

**新增 API**

| API | 说明 |
| --- | --- |
| [`requestLLM`](https://pub.dev/documentation/nertc_core/latest/nertc/NERtcEngine/requestLLM.html) | 发送请求给大型语言模型，通过 `onAiData` 返回数据。

**兼容性**

升级 NERtc SDK 依赖至 5.9.20 版本。

## 5.9.11 (2025-12-15)

**新增功能**

- 视频能力：
    - 新增 `setVideoStreamLayerCount` 方法，支持自定义设置视频流的分层模式。
    - 新增 `setExternalAudioSource` / `pushExternalAudioFrame` 方法，支持推送外部音频数据。
    - 新增 `setExternalSubStreamAudioSource` / `pushExternalSubAudioFrame` 方法，支持辅流音频输入。

- 音频能力：
    - 新增 `setAINSMode` 方法，支持设置 AI 智能降噪模式，提供更优质的音频通话体验。
    - 新增空间音效功能。

- 数据通道：
    - 支持开启本地、订阅远端、以及发送自定义数据通道。

- 直播推流与播放：
    - 支持推送/停止推送 RTMP 流。
    - 支持直播播放控制能力，包括暂停/恢复/停止/静音等操作。

- 实时字幕：
    - 新增 `startASRCaption` 方法，开启实时语音识别字幕。
    - 新增 `stopASRCaption` 方法，关闭字幕功能。
    - 支持多语言实时转写。

- 子房间功能：
    - 支持在已加入的 RTC 频道基础上创建新的子频道，实现多房间并行通信能力。

- 本地录制（macOS/Windows）：

    - 支持录制流管理。
    - 支持录制格式转换。

- 多路径传输（Android/macOS）：
    - 新增 `setMultiPathOption` 方法支持网络多路径传输。

## 5.9.0 (2025-09-25)

**兼容性**

升级 NERtc SDK 依赖至 5.9.11 版本。

## 5.8.23 (2025-07-31)

**新增功能**

新增支持 macOS、Windows 平台，让开发者可以在不同操作系统应用开发间无缝切换调用接口。

**兼容性**

升级 NERtc SDK 依赖至 5.8.23 版本。

## 5.8.15 (2025-05-28)

**新增功能**

- 支持 iOS ARM64 架构模拟器。开发者现在可以在 Apple Silicon Mac 上使用 ARM64 架构的 iOS 模拟器进行开发和测试，提升开发效率。
- 支持 iOS 屏幕录制/共享功能。支持在 iOS 应用中实现屏幕共享功能，适用于在线会议、远程教学、协作办公等场景。详情请参考 [屏幕共享](https://doc.yunxin.163.com/nertc/guide/jEzMjQ5MTA?platform=flutter)。

**兼容性**

升级 NERTC SDK 依赖版本至 [5.8.15](https://doc.yunxin.163.com/nertc/concept/TE5MzI1MzA?platform=client#5815-2025-04-29)，带来更好的性能和稳定性。

## 5.5.101 (2023-12-07)

**新增功能**

新增支持 [高级 Token 鉴权](https://doc.yunxin.163.com/nertc/server-apis/DU3Mjk0MzQ?platform=server) 功能。

**新增 API**

| API | 说明 |
| --- | --- |
| [updatePermissionKey](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/updatePermissionKey.html) | 更新权限密钥。 |
| [onPermissionKeyWillExpire](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onPermissionKeyWillExpire.html) | 权限密钥即将过期事件回调。 |
| [onUpdatePermissionKey](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUpdatePermissionKey.html) | 更新权限密钥事件回调。 |

**改进优化**

- **更新错误码**：[NERtcErrorCode](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcErrorCode-class.html)。
- **开发环境**：解决 iOS 的 info.plist 中的 bundle version 问题。

**兼容性**

升级 NERTC SDK 依赖版本至 5.5.10。

## 5.4.7 (2023-08-31)

**新增功能**

| 新增功能 | 特性描述 |
| --- | --- |
| [自定义视频采集](https://doc.yunxin.163.com/nertc/guide/jIwOTE5MzM?platform=flutter) | 支持外部视频源数据输入。 |

**新增 API**

| API | 说明 |
| --- | --- |
| [setExternalVideoSource](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setExternalVideoSource.html) | 开启外部视频源数据输入 |
| [pushExternalVideoFrame](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/pushExternalVideoFrame.html) | 推送外部视频数据帧 |

**问题修复**

修复部分已知问题。

## 5.4.0 (2023-07-18)

**改进优化**

- **AI 降噪能力优化**：提升了人声音质和降噪量，有效抑制各种噪声而不损伤人声。在教育和会议场景中，对人声（如小孩声和笑声）进行了保护，避免过度抑制。

- **AEC 算法优化**：重点改进本端和远端双讲时的效果，在双讲场景下保留清晰流畅的近端人声，提供更舒适的会议和语聊体验。

- **弱网环境优化**：
    - 通过优化音频 NACK 请求，降低弱网环境下的端到端音频延时。
    - 优化弱网环境下视频首帧耗时。
    - 改善极端弱网环境下的视频清晰度。

- **Android 平台优化**：

    - 默认使用 camera2，提升摄像头图像采集质量。
    - 加强硬件功能和编解码质量的稳定性，支持更多手机设备。
    - 优化 NE264 编码器性能。
    - 改善低端机前处理帧率和编码稳定性，提升视频发送帧率。

- **权限处理优化**：当用户未赋予 `BLUETOOTH_CONNECT` 权限时，支持使用手机麦克风采集声音。

**问题修复**

修复部分已知问题。

**兼容性**

升级 NERTC SDK 依赖版本至 5.4.0。

## 4.6.52-rc.1 (2023-05-30)

**问题修复**

- 修复了 iOS 美颜设置不生效的问题。
- 修复了 `NERtcVideoView` 画布填充参数不生效的问题。
- 修复了网络状态监听回调缺失的问题。

## 4.6.52-rc.0 (2023-05-19)

**新增 API**

4.6.52 版本新增的接口请参考 [Flutter API 参考](https://doc.yunxin.163.com/nertc/client-apis/DAxOTQ3MzA?platform=flutter)。

**变更 API**

| 接口变更 | 说明 |
| ---- | ---- |
| 设置本地视图 | `attachToLocalVideo` 接口已废弃，请替换为新接口：[`NERtcVideoView`](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoView-class.html) |
| 设置远端视图 | `attachToRemoteVideo` 接口已废弃，请替换为新接口：[`NERtcVideoView`](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoView-class.html) |
| 订阅远端用户的视频流 | 接口名称已更新：<br>`subscribeRemoteVideo` → [`subscribeRemoteVideoStream`](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeRemoteVideoStream.html) |

**兼容性**

升级 NERTC SDK 依赖版本至 4.6.52。

## 3.9.0 (2021-01-26)

NERTC Flutter SDK 正式发布。

- 搭建基于原生 SDK 的 Flutter 框架。
- 支持标准的多人音视频能力，包括音视频的发送、订阅、质量数据透明。