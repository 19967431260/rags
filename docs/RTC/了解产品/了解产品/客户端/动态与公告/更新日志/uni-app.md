本文介绍网易云信音视频通话 SDK（NERTC SDK）基于 UniApp 开发框架的更新日志。具体功能请前往 [下载 SDK](https://doc.yunxin.163.com/nertc/resource?platform=uniapp) 和 查看 [API 文档](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/index.html)。

## 5.6.38 (2025-11-04)

**新增特性**

- 增加 AI 任务支持实时字幕、AI 打断功能。您可以参考 [`startASRCaption`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#startasrcaption)。
- 增加音频手动订阅能力。您可以参考 [`setParameters`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setparameters) 和 [`subscribeRemoteAudioStream`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#subscriberemoteaudiostream)。

## 5.6.37 (2025-10-14)

**优化**

- 优化演示 Demo（方便接入美颜滤镜）。
- 优化 iOS 端设置滤镜强度的流程，对齐安卓端。

## 5.6.36 (2025-08-25)

**修复缺陷**

修复安卓端美颜效果设置混乱的问题。

## 5.6.35 (2024-12-10)

- 新增 iOS 端屏幕共享功能。您可以参考 [setupShareKit](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setupsharekit) 和 [屏幕共享](https://doc.yunxin.163.com/nertc/guide/TI5MjQzNjY?platform=uniapp) 接入已有项目。 
- 新增适配 Vue3.0 开发框架的 Demo 文件。您可以参考 [下载 SDK 和示例代码](https://doc.yunxin.163.com/nertc/guide/zUyNzEwOTQ?platform=uniapp) 获取。

## 5.6.34 (2024-11-04)

新增视频截图功能。您可以参考 [API 文档](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/index.html#%E6%88%AA%E5%9B%BE) 和 [视频截图](https://doc.yunxin.163.com/nertc/guide/jU5MjMwNjE?platform=uniapp) 接入已有项目。 

## 5.6.33 (2024-10-25)

新增自研美颜特效（简称 **云信美颜**）功能，帮助用户在音视频通话或互动直播场景中，对人脸进行美肤、美型等美颜调整，并增加效果滤镜。您可以参考 [API 文档](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/index.html#%E4%BA%91%E4%BF%A1%E7%BE%8E%E9%A2%9C) 和 [云信美颜](https://doc.yunxin.163.com/nertc/guide/jYwMjY1NDA) 接入已有项目。 

## 5.6.0 (2024-06-04)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`startAudioMixing`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#startaudiomixing) | 开始伴音 |
| [`stopAudioMixing`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#stopaudiomixing) | 结束伴音 |
| [`pauseAudioMixing`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#pauseaudiomixing) | 暂停伴音 |
| [`resumeAudioMixing`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#resumeaudiomixing) | 恢复伴音 |
| [`setAudioMixingPlaybackVolume`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setaudiomixingplaybackvolume) | 设置伴音文件的播放音量 |
| [`setAudioMixingSendVolume`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setaudiomixingsendvolume) | 设置伴音文件的发送音量 |
| [`getAudioMixingPlaybackVolume`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#getaudiomixingplaybackvolume) | 获取伴音文件的播放音量 |
| [`getAudioMixingSendVolume`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#getaudiomixingsendvolume) | 获取伴音文件的发送音量 |
| [`getAudioMixingDuration`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#getaudiomixingduration) | 获取伴音的总长度 |
| [`setAudioMixingPosition`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setaudiomixingposition) | 设置伴音文件的播放进度 |
| [`getAudioMixingCurrentPosition`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#getaudiomixingcurrentposition) | 获取伴音文件的当前播放进度 |
| [`getAudioMixingPitch`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#getaudiomixingpitch) | 获取伴音文件的音调 |
| [`setAudioMixingPitch`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setaudiomixingpitch) | 设置伴音文件的音调 |
| [`onAudioMixingStateChanged`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/interfaces/nertccallback.nertccallback-1.html#onaudiomixingstatechanged) | 本地用户的伴音文件播放状态改变回调 |
| [`onAudioMixingTimestampUpdate`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/interfaces/nertccallback.nertccallback-1.html#onaudiomixingtimestampupdate) | 伴音文件播放进度回调 |
| [`changeVideoCanvas`](https://doc.yunxin.163.com/nertc/references/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#changevideocanvas) | 交换本端和远端视频的视图 |

**改进优化**

- 增加 音频伴音功能。
- 增加 1 对 1 场景下大小视图动态切换能力。
- 底层引擎升级至 v5.6.0。

## 5.5.21 (2024-02-04)

**新增 API**

| 接口/回调 | 接口/回调说明 |
| ---- | ---- |
| [`setParameters`](https://doc.yunxin.163.com/nertc/api-refer/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#setparameters) | 设置音视频通话的相关参数。 |
| [`enableLoopbackRecording`](https://doc.yunxin.163.com/nertc/api-refer/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#enableloopbackrecording) | 是否开启音频共享（即系统声音）。 |
| [`adjustLoopBackRecordingSignalVolume`](https://doc.yunxin.163.com/nertc/api-refer/uniapp/typedoc/Latest/zh/html/modules/nertc.nertc-1.html#adjustloopbackrecordingsignalvolume) | 设置音频共享的音量。 |

**改进优化**

- 增加 AI 降噪功能。
- 增加 系统音频共享能力支持（安卓端）。
- 优化插件包体积，缩小至 1/10 左右。

**问题修复**
- 修复 `setLocalVideoConfig` 接口报错的问题
- 修复测试 Demo 上的一些特殊场景下的异常

## 5.5.11 (2023-12-15)

**改进优化**

- 增加 String 格式的 userID，用于支持其超过 Number 数据类型范围的场景。
- 支持 H5 平台。

## 5.3.8002 (2023-09-25)

**改进优化**

调整 Android 系统中 video 视图的覆盖逻辑，废弃 `isMediaOverlay` 参数，调整后的逻辑请参考 [设置视频属性](https://doc.yunxin.163.com/nertc/guide/jA0Nzk5MDY?platform=uniapp#点对点通话视图覆盖)。

## 5.3.8001 (2023-08-03)

**改进优化**

uid 支持更大的数值范围，从 2<sup>31</sup> 扩充到 2<sup>53</sup>。

## 5.3.8 (2023-08-03)

底层 NERTC 引擎升级至 V5.3.8 版本。

## 5.3.7 (2023-07-18)

首次发布，基于 NERTC Native 端 V5.3.7 版本的接口进行封装，包括实时音视频通话、设置音频属性、设置视频属性、设置通话音量、屏幕共享、监测发言者音量、通话中质量监测、耳返、摄像头切换和音频设备管理等功能。

请在 [网易云信 SDK 下载中心](https://doc.yunxin.163.com/nertc/sdk-download) 下载最新的 UniApp 版本。