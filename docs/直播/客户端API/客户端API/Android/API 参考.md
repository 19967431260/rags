网易云信将直播服务与音视频服务进行了深度融合，为用户提供一个最佳的 CDN 直播方案。您可以通过集成特定版本的 RTC SDK 实现 CDN 推流。本文列举 RTC SDK 中直播推流相关的关键 API，更多 API 接口请参见[音视频通话2.0 API参考](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/index.html)。

## 直播推流

| 方法 | 功能 | 起始版本 |
|---|---|---|
|  [NERtcEx#addLiveStreamTask()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ad2041ecad6d89313da6c52b34f1a36a3)| 添加旁路推流任务 | V3.5.0 |
| [NERtcEx#updateLiveStreamTask()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#a03076e65c0123a135780fd34d7c58321) | 更新修改旁路推流任务 | V3.5.0 |
| [NERtcEx#removeLiveStreamTask()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac72c0e04551af133cec49a1dc0b7aabc) | 删除旁路推流任务 | V3.5.0 |
| [NERtcEx#startPushStreaming()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ac6105aef79bc3cbcd5be568ad00edd03)| 开始 CDN 推流 | V4.6.420 |
| [NERtcEx#stopPushStreaming()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aadb99d2bd5950ca7cfb1b39b21d30ca0) | 停止 CDN 推流 | V4.6.420 |



| 事件 | 描述 | 起始版本 |
|---|---|---|
| [NERtcCallbackEx#onStartPushStreaming()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a4bfe88f634363ffb7cb58494a8651a40)| 开始 CDN 推流的结果回调 | V4.6.420 |
| [NERtcCallbackEx#onStopPushStreaming()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a3f4dbef8d72e6d3b222108ab918a31e9) | 停止CDN 推流的结果回调 | V4.6.420 |
| [NERtcCallbackEx#onPushStreamingReconnecting()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a1806b650982aac752c1225bf93ae488e)| CDN 推流中断，变为重连中状态的回调 | V4.6.420 |
| [NERtcCallbackEx#onPushStreamingReconnectedSuccess()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a6793656a53ceefbeb020844690ed925b) | CDN 推流中断后，重连成功的回调 | V4.6.420 |
| [NERtcCallbackEx#onDisconnect()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback.html#ac1502d885a8114de4532a7a84ac66cdb)| CDN 推流中断后，重连失败并断开的回调 | V3.5.0 |

## 跨房间流媒体转发

| 方法 | 功能 | 起始版本 |
|---|---|---|
| [NERtcEx#startChannelMediaRelay()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aab6a2600bd3799a6a500610989f61c5a) | 开始跨房间媒体流转发。 | V4.2.1 |
| [NERtcEx#updateChannelMediaRelay()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#ae4f5b5827d6b23fe062d2b4726934844) | 更新媒体流转发的目标房间。 | V4.2.1 |
| [NERtcEx#stopChannelMediaRelay()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/classcom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_ex.html#aefe628b0f3b1aac7b9f9f61ee0c502c1) | 停止跨房间媒体流转发。 | V4.2.1 |


| 事件 | 描述 | 起始版本 |
|---|---|---|
| [NERtcCallbackEx#onMediaRelayStatesChange()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a50b06dedbdb5840f45ba02803773f1f8) | 跨房间媒体流转发状态发生改变回调。 | V4.2.1 |
| [NERtcCallbackEx#onMediaRelayReceiveEvent()](https://doc.yunxin.163.com/docs/interface/nertc/android/doxygen/Latest/zh/html/interfacecom_1_1netease_1_1lava_1_1nertc_1_1sdk_1_1_n_e_rtc_callback_ex.html#a2b64c4992afc0e759b729b92341c3191) | 媒体流相关转发事件回调。 | V4.2.1 |
