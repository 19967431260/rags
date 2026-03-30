本文介绍直播推流 SDK Android 端的更新日志。

:::note notice
推流 SDK 已停止迭代。建议您替换为网易云信音视频通话 SDK（NERTC SDK），并选择 [5.6.10 版本](https://doc.yunxin.163.com/nertc/concept/TE5MzI1MzA?platform=client#v5610-2024-06-14) 实现直播推流效果。您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。
:::

## 4.6.421 (2023-10-16)

**问题修复**

修复部分已知问题。

## 4.6.420 (2023-05-06)

**新增特性**

| 新增特性 | 特性描述 | 相关文档
| ---- | ---- | ---- |
| RTC 支持 CDN 推流 | NERTC SDK 融合了 CDN 推流能力，您只要集成一个 SDK 即可实现单人直播、PK 直播和连麦，且三个场景之间能无缝切换，提升 PK 直播体验。 | [快速实现 CDN 推流](https://doc.yunxin.163.com/live-streaming/docs/zkwOTcwODI) |

**新增 API**

| 接口/回调 | 接口/回调说明 |
| --- | --- |
| [NERtcEx#startPushStreaming()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac6105aef79bc3cbcd5be568ad00edd03) | 开始 CDN 推流 |
| [NERtcEx#stopPushStreaming()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aadb99d2bd5950ca7cfb1b39b21d30ca0) | 停止 CDN 推流 |
| [NERtcCallbackEx#onStartPushStreaming()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a4bfe88f634363ffb7cb58494a8651a40) | 开始 CDN 推流的结果回调 |
| [NERtcCallbackEx#onStopPushStreaming()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a3f4dbef8d72e6d3b222108ab918a31e9) | 停止 CDN 推流的结果回调 |
| [NERtcCallbackEx#onPushStreamingReconnecting()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a1806b650982aac752c1225bf93ae488e) | CDN 推流中断，变为重连中状态的回调 |
| [NERtcCallbackEx#onPushStreamingReconnectedSuccess()](https://doc.yunxin.163.com/nertc/api-refer/android/doxygen/V4.6.420/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a6793656a53ceefbeb020844690ed925b) | CDN 推流中断后，重连成功的回调 |