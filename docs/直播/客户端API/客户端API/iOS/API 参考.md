网易云信将直播服务与音视频服务进行了深度融合，为用户提供一个最佳的 CDN 直播方案。您可以通过集成特定版本的 RTC SDK 实现 CDN 推流。本文列举 RTC SDK 中直播推流相关的关键 API，更多 API 接口请参考 [音视频通话2.0 API参考](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/index.html)。

## 直播推流

| 方法 | 描述 | 起始版本 |
|---|---|---|
| [INERtcEngineEx#startPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#ab56487379a9f24480c550f7635ed7581)| 开始 CDN 推流 | V4.6.420 |
| [INERtcEngineEx#stopPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#a09d6a75c91de83dd1e07bddc375a3e2a) | 停止 CDN 推流 | V4.6.420 |
| [INERtcEngineEx#addLiveStreamTask](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#a2fb07bf756073c68f8625ce5dbc51792)| 添加旁路推流任务 | V3.5.0 |
| [INERtcEngineEx#updateLiveStreamTask](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#aa4c548c7ce5ffe86760623a11ca88993) | 更新修改旁路推流任务 | V3.5.0 |
| [INERtcEngineEx#removeLiveStreamTask](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#ab2f98e936a96622664b425c0d78f7c0c) | 删除旁路推流任务 | V3.5.0 |



| <div style="width:300PX">事件</div> | <div style="width:200PX">描述</div> | 起始版本 |
|---|---|---|
| [NERtcEnginePushStreamingObserver#onNERtcEngineStartPushStreamingWithResult](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a9bcaefade260397f639eb2b95ca03cf3) | 开始 CDN 推流的结果回调 | V4.6.420 |
| [NERtcEnginePushStreamingObserver#onNERtcEngineStopPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#aaa23881088a90a5461018e362ab6e2cf) | 停止 CDN 推流的结果回调 | V4.6.420 |
| [NERtcEnginePushStreamingObserver#onNERtcEnginePushStreamingChangeToReconnectingWithReason](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a4eb9da2908d15c3d76ed134fd9977672) | CDN 推流中断，变为重连中状态的回调 | V4.6.420 |
| [NERtcEnginePushStreamingObserver#onNERtcEnginePushStreamingReconnectedSuccess](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a645d36181e6e006fadcbc001cbd10d9d) | CDN 推流中断后，重连成功的回调 | V4.6.420 |
| [NERtcEngineDelegate#onNERtcEngineDidDisconnectWithReason](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_delegate-p.html#aa1a3d63904a172a1675e01cbdd1f4399)| CDN 推流中断后，重连失败并断开的回调 | V3.5.0 |



## 跨房间流媒体转发
| 方法 | 描述 | 起始版本 |
|---|---|---|
| [INERtcEngineEx#startChannelMediaRelay](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#ab3d653209bd00c180dbe4b12104095b4) | 开始跨房间媒体流转发 | V4.2.1 |
| [INERtcEngineEx#updateChannelMediaRelay](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#abf62167dd122c8ccaf0e9f65ac662a79)| 更新媒体流转发的目标房间。 | V4.2.1 |
| [INERtcEngineEx#stopChannelMediaRelay](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#a613db50db64a1d10e7341ff34a47e40f) | 停止跨房间媒体流转发。 | V4.2.1 |



| <div style="width:300PX">事件</div> | <div style="width:200PX">描述</div> | 起始版本 |
|---|---|---|
| [NERtcEngineDelegateEx#onNERtcEngineChannelMediaRelayStateDidChange](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_delegate_ex-p.html#a4334e33d7eb53442103380db4dd1af09) | 跨房间媒体流转发状态发生改变的回调。 | V4.2.1 |
| [NERtcEngineDelegateEx#onNERtcEngineDidReceiveChannelMediaRelayEvent](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/Latest/zh/html/protocol_n_e_rtc_engine_delegate_ex-p.html#a23e9681488a7ba3130ee6b73c266b6d9) | 跨房间媒体流相关转发事件的回调。 | V4.2.1 |

