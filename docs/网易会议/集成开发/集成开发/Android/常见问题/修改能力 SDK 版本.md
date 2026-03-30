本文主要介绍如何修改会议组件底层的能力 SDK 版本。

### 底层依赖

网易会议组件中依赖了网易云信的 [即时通讯 NIM SDK（简称 NIM SDK）](https://doc.yunxin.163.com/messaging2/concept?platform=client) 和 [音视频通话 2.0 SDK（简称 NERTC SDK）](https://doc.yunxin.163.com/nertc/concept?platform=client) 的底层能力。您可以在网易会议组件的 [更新日志](https://doc.yunxin.163.com/meeting/guide/zk0MjM1OTg?platform=android) 中，查看到对应组件版本适配的 NIM SDK 和 NERTC SDK 版本。

<!-- 但在极少的场景下，会出现切换 NIM SDK 和 NERTC SDK 版本的需求。 -->

如果您的项目中已经单独集成了 NIM SDK 和 NERTC SDK，并与 NEMeetingKit 中的版本冲突时，您可以手工指定 NIM SDK 和 NERTC SDK 的版本号。具体实现方式，请参考《功能版本与 SDK 依赖对照》[修改能力 SDK 版本](https://doc.yunxin.163.com/meeting/guide/DgyMzAyNDI?platform=android#override) 章节。

### 音视频相关

如果您的应用中同时需要使用网易会议组件（NEMeetingKit）和 NERTC SDK 或呼叫组件时，由于它们都依赖了 NERTC SDK，可能会产生冲突。请参考《功能版本与 SDK 依赖对照》[与 NERTC SDK 和呼叫组件共存](https://doc.yunxin.163.com/meeting/guide/DgyMzAyNDI?platform=android#conflict) 了解如何处理音视频相关组件的冲突问题，避免因多组件依赖 NERTC SDK 而产生的冲突问题，确保应用稳定运行。