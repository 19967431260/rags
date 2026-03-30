本文介绍直播推流 iOS 端的更新日志。

:::note notice
推流 SDK 已停止迭代。建议您替换为网易云信音视频通话 SDK（NERTC SDK），并选择 [5.6.10 版本](https://doc.yunxin.163.com/nertc/concept/TcyMzY0ODg?platform=client#v5610-2024-06-14) 实现直播推流效果。您可以仅集成 NERTC SDK，用更少的 API 调用，就实现秀场直播的典型场景。
:::

## [4.6.421] - 2023-10-16

### 问题修复
修复部分已知问题。

## [4.6.420] - 2023-05-06
### 新增特性
| 序号 | 新增特性       | 特性描述                                                           |相关文档
|------|----------------|--------------------------------------------------------------------|---------
| 1    |RTC 支持 CDN 推流     |NERTC SDK 融合了 CDN 推流能力，您只要集成一个 SDK 即可实现单人直播、PK 直播和连麦，且三个场景之间能无缝切换，提升 PK 直播体验。 |[快速实现 CDN 推流](https://doc.yunxin.163.com/live-streaming/docs/Dc4MDAwMzM?platform=iOS)  |


### 新增API


| 接口/回调                       |    <div style="width:200PX">接口/回调说明</div>                            |
|---|---|
| [INERtcEngineEx#startPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#ab56487379a9f24480c550f7635ed7581)| 开始 CDN 推流 | 
| [INERtcEngineEx#stopPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_i_n_e_rtc_engine_ex-p.html#a09d6a75c91de83dd1e07bddc375a3e2a) | 停止 CDN 推流 | 
| [NERtcEnginePushStreamingObserver#onNERtcEngineStartPushStreamingWithResult](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a9bcaefade260397f639eb2b95ca03cf3) | 开始 CDN 推流的结果回调 | 
| [NERtcEnginePushStreamingObserver#onNERtcEngineStopPushStreaming](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#aaa23881088a90a5461018e362ab6e2cf) | 停止 CDN 推流的结果回调 | 
| [NERtcEnginePushStreamingObserver#onNERtcEnginePushStreamingChangeToReconnectingWithReason](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a4eb9da2908d15c3d76ed134fd9977672) |  CDN 推流中断，变为重连中状态的回调 | 
| [NERtcEnginePushStreamingObserver#onNERtcEnginePushStreamingReconnectedSuccess](https://doc.yunxin.163.com/nertc/api-refer/iOS/doxygen/V4.6.420/zh/html/protocol_n_e_rtc_engine_push_streaming_observer-p.html#a645d36181e6e006fadcbc001cbd10d9d) |  CDN 推流中断后，重连成功的回调 | 
