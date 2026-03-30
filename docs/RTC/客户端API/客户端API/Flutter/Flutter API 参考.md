网易云信 NERTC SDK 提供完善的音视频通话开发框架，提供基于网络的视频通话和语音通话功能，还提供多人视频和音频会议功能，支持通话中音视频设备控制和实时音视频模式切换，支持视频采集数据回调以实现美颜等自定义功能。

网易云信音视频通话 SDK（简称 NERTC SDK） Flutter 端的 API 文档请单击 [此处](https://pub.dev/documentation/nertc_core/latest/nertc) 查看最新的 API。

<!--历史

## 接口类

- [NERtcEngine](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine-class.html) 类包含应用程序调用的主要方法。
- [NERtcDeviceManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager-class.html ) 类包含设备调用的主要方法。
- [NERtcVideoView](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoView-class.html)类包含视频管理的 Flutter 单独封装的方法。
- [NERtcAudioMixingManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager-class.html ) 类包含伴音调用的主要方法。
- [NERtcAudioEffectManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager-class.html ) 类包含音效调用的主要方法。
- [NERtcChannelEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback-class.html ) 类用于向应用程序发送用户状态回调通知。
- [NERtcDeviceEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceEventCallback-class.html ) 类用于向应用程序发送设备状态回调通知。
- [NERtcAudioMixingEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingEventCallback-class.html ) 类用于向应用程序发送伴音状态回调通知。
- [NERtcAudioEffectEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectEventCallback-class.html ) 类用于向应用程序发送音效状态回调通知。
- [NERtcStatsEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback-class.html ) 接口类用于向应用程序发送媒体状态类回调通知。

<style>
table th:first-of-type {
    width: 30%;
}
table th:nth-of-type(2) {
    width: 50%;
}
table th:nth-of-type(3) {
    width: 15%;
}
</style>

## 房间管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [create](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/create.html) | 创建 NERTC 实例。 | 3.9.0 |
| [release](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/release.html) | 销毁 NERTC 实例，释放资源。 | 3.9.0 |
| [setChannelProfile](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setChannelProfile.html) | 设置房间场景。如果需要设置房间场景，必须在调用 create 之后、调用 joinChannel 之前调用此接口。 | 3.9.0 |
| [setClientRole](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setClientRole.html) | 设置用户角色。 | 3.9.0 |
| [joinChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/joinChannel.html) | 加入房间。 | 3.9.0 |
| [leaveChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/leaveChannel.html) | 离开房间。 | 3.9.0 |
| [getConnectionState](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/getConnectionState.html) | 主动获取网络连接状态。 | 3.9.0 |
| [switchChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/switchChannel.html) | 快速切换音视频房间。 | 4.6.52 |
| [setParameters](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setParameters.html) | 设置音视频通话的相关参数。此接口提供技术预览或特别定制功能。 | 4.6.52 |
| [getConnectionState](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/getConnectionState.html) | 获取连接状态。 | 4.6.52 |
| [updatePermissionKey](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/updatePermissionKey.html) | 更新权限密钥。 | 4.6.52 |

## 房间事件

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [onJoinChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onJoinChannel.html) | 加入房间回调。 | 3.9.0 |
| [onLeaveChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLeaveChannel.html) | 退出房间回调。 | 3.9.0 |
| [onUserJoined](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserJoined.html) | 远端用户加入当前房间回调。 | 3.9.0 |
| [onUserLeave](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserLeave.html) | 远端用户离开当前房间回调。 | 3.9.0 |
| [onReJoinChannel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onReJoinChannel.html) | 重新加入房间回调。 | 3.9.0 |
| [onClientRoleChange](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onClientRoleChange.html) | 用户角色已切换回调。 | 3.9.0 |
| [onConnectionStateChanged](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onConnectionStateChanged.html) | 网络连接状态已改变回调。 | 3.9.0 |
| [onConnectionTypeChanged](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onConnectionTypeChanged.html) | 本地网络类型已改变回调。 | 3.9.0 |
| [onDisconnect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onDisconnect.html) | 从房间断开的回调。 | 3.9.0 |
| [onReconnectingStart](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onReconnectingStart.html) | 重连开始回调。 | 3.9.0 |

## 音频管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setAudioProfile](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setAudioProfile.html) | 设置音频编码配置 | 3.9.0 |
| [adjustRecordingSignalVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/adjustRecordingSignalVolume.html) | 调节录音音量 | 3.9.0 |
| [adjustPlaybackSignalVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/adjustPlaybackSignalVolume.html) | 调节播放音量 | 3.9.0 |
| [adjustUserPlaybackSignalVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/adjustUserPlaybackSignalVolume.html) | 调节本地播放的指定远端用户的信号音量。 | 4.6.52 |
| [enableLocalAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableLocalVideo.html) | 开关本地音频采集 | 3.9.0 |
| [muteLocalAudioStream](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/muteLocalAudioStream.html) | 开关本地音频发送 | 3.9.0 |
| [subscribeRemoteAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeRemoteAudio.html) | 订阅／取消订阅指定音频流 | 3.9.0 |
| [subscribeAllRemoteAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeAllRemoteAudio.html) | 订阅／取消订阅所有远端音频流 | 3.9.0 |
| [setRemoteHighPriorityAudioStream](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setRemoteHighPriorityAudioStream.html) | 设置远端用户音频流的高优先级 | 4.6.52 |
| [enableLoopbackRecording](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableLoopbackRecording.html) | 开启或关闭音频共享 | 4.6.52 |
| [adjustLoopBackRecordingSignalVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/adjustLoopBackRecordingSignalVolume.html) | 调整共享音频音量 | 4.6.52 |
| [enableLocalSubStreamAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableLocalSubStreamAudio.html) | 开启或关闭音频辅流 | 4.6.52 |
| [subscribeRemoteSubStreamAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeRemoteSubStreamAudio.html) | 取消或恢复订阅指定远端用户的音频主流 | 4.6.52 |
| [muteLocalSubStreamAudio](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/muteLocalSubStreamAudio.html) | 静音或解除静音本地上行的音频辅流 | 4.6.52 |
| [setAudioSubscribeOnlyBy](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setAudioSubscribeOnlyBy.html) | 设置自己的音频只能被房间内指定的人订阅 | 4.6.52 |
| [enableMediaPub](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableMediaPub.html) | 开启或关闭本地媒体流（主流）的发送 | 4.6.52 |

## 音频事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onAudioHasHowling](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onAudioHasHowling.html) | 检测到啸叫回调 | 3.9.0 |

## 视频管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [enableLocalVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableLocalVideo.html) | 开关本地视频 | 3.9.0 |
| [setLocalVideoConfig](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalVideoConfig.html) | 设置视频发送配置 | 3.9.0 |
| [startVideoPreview](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startVideoPreview.html) | 开启视频预览 | 3.9.0 |
| [stopVideoPreview](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopVideoPreview.html) | 停止视频预览 | 3.9.0 |
| [muteLocalVideoStream](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/muteLocalVideoStream.html) | 开关本地视频发送 | 3.9.0 |
| [subscribeRemoteVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeRemoteVideo.html) | 订阅 / 取消订阅指定远端用户的视频流 | 3.9.0 |
| [attachToLocalVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToLocalVideo.html) | 关联本地用户视频视图 | 3.9.0 |
| [attachToRemoteVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToRemoteVideo.html) | 关联远端用户视频视图 | 3.9.0 |
| [setCameraCaptureConfig](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setCameraCaptureConfig.html) | 设置本地摄像头的采集偏好等配置 | 4.6.52 |
| [enableSuperResolution](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableSuperResolution.html) | 启用或停止 AI 超分 | 4.6.52 |
| [attachToRemoteSubStreamVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToRemoteSubStreamVideo.html) | 添加为远端用户辅流视频画布 | 4.6.52 |
| [attachToLocalSubStreamVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToLocalSubStreamVideo.html) | 添加为本地用户辅流视频画布 | 4.6.52 |
| [enableVirtualBackground](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableVirtualBackground.html) | 开启/关闭虚拟背景 | 4.6.52 |
| [enableVideoCorrection](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableVideoCorrection.html) | 是否启用视频图像畸变矫正 | 4.6.52 |
| [setVideoCorrectionConfig](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setVideoCorrectionConfig.html) | 设置视频图像矫正参数 | 4.6.52 |
| [setMirror](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/setMirror.html) | 设置画面是否镜像 | 4.6.52 |
| [setExternalVideoSource](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setExternalVideoSource.html) | 开启外部视频源数据输入 | 5.4.7 |
| [pushExternalVideoFrame](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/pushExternalVideoFrame.html) | 推送外部视频数据帧 | 5.4.7 |

## 本地媒体事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onFirstAudioFrameDecoded](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onFirstAudioFrameDecoded.html) | 已解码远端音频首帧的回调 | 3.9.0 |
| [onFirstVideoFrameDecoded](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onFirstVideoFrameDecoded.html) | 已解码远端视频首帧的回调 | 3.9.0 |
| [onFirstAudioDataReceived](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onFirstAudioDataReceived.html) | 远端音频首帧回调 | 3.9.0 |
| [onFirstVideoDataReceived](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onFirstVideoDataReceived.html) | 远端视频首帧回调 | 3.9.0 |
| [onMediaRightChange](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onMediaRightChange.html) | 服务端禁言音视频权限变化回调 | 4.6.52 |
| [onVirtualBackgroundSourceEnabled](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onVirtualBackgroundSourceEnabled.html) | 通知虚拟背景是否成功开启的回调 | 4.6.52 |

## 远端媒体事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onUserVideoMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserVideoMute.html) | 远端用户关闭视频发送的回调 | 3.9.0 |
| [onUserAudioMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserAudioMute.html) | 远端用户关闭音频发送的回调 | 3.9.0 |
| [onUserAudioStart](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserAudioStart.html) | 远端用户开启音频的回调 | 3.9.0 |
| [onUserAudioStop](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserAudioStop.html) | 远端用户关闭音频的回调 | 3.9.0 |
| [onUserVideoStart](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserVideoStart.html) | 远端用户开启视频的回调 | 3.9.0 |
| [onUserVideoStop](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserVideoStop.html) | 远端用户关闭视频的回调 | 3.9.0 |
| [onUserSubStreamAudioMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserSubStreamAudioMute.html) | 远端用户暂停或恢复发送音频辅流的回调 | 4.6.52 |
| [onUserSubStreamAudioStart](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserSubStreamAudioStart.html) | 远端用户开启音频辅流回调 | 4.6.52 |
| [onUserSubStreamAudioStop](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserSubStreamAudioStop.html) | 远端用户停用音频辅流回调 | 4.6.52 |

## 数据统计事件

SDK 定期向 App 报告以下统计信息，每 2 秒触发一次。

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [setStatsEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setStatsEventCallback.html) | 设置统计信息回调 | 3.9.0 |
| [clearStatsEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/clearStatsEventCallback.html) | 清除统计信息回调 | 3.9.0 |
| [onRtcStats](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onRtcStats.html) | 当前通话统计回调，每 2 秒触发一次 | 3.9.0 |
| [onNetworkQuality](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onNetworkQuality.html) | 通话中每个用户的网络上下行质量报告回调 | 3.9.0 |
| [onLocalAudioStats](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onLocalAudioStats.html) | 本地音频流统计信息回调 | 3.9.0 |
| [onLocalVideoStats](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onLocalVideoStats.html) | 本地视频流统计信息回调 | 3.9.0 |
| [onRemoteAudioStats](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onRemoteAudioStats.html) | 通话中远端音频流的统计信息回调 | 3.9.0 |
| [onRemoteVideoStats](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcStatsEventCallback/onRemoteVideoStats.html) | 通话中远端视频流的统计信息回调 | 3.9.0 |

## 视频大小流

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [enableDualStreamMode](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableDualStreamMode.html) | 设置是否开启视频大小流模式 | 3.9.0 |
| [setLocalPublishFallbackOption](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalPublishFallbackOption.html) | 设置弱网条件下发布的音视频流回退选项 | 4.6.52 |
| [setRemoteSubscribeFallbackOption](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setRemoteSubscribeFallbackOption.html) | 设置弱网条件下订阅的音视频流回退选项。 | 4.6.52 |

## 视频大小流事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onLocalPublishFallbackToAudioOnly](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLocalPublishFallbackToAudioOnly.html) | 本地发布流已回退为音频流、或已恢复为音视频流回调。 | 4.6.52 |
| [onRemoteSubscribeFallbackToAudioOnly](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onRemoteSubscribeFallbackToAudioOnly.html) | 订阅的远端流已回退为音频流、或已恢复为音视频流回调。 | 4.6.52 |

## 通话前网络测试

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [startLastmileProbeTest](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startLastmileProbeTest.html) | 开始通话前网络质量探测。 | 4.6.52 |
| [stopLastmileProbeTest](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopLastmileProbeTest.html) | 停止通话前网络质量探测。 | 4.6.52 |


## 通话前网络质量探测事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onLastmileQuality](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLastmileQuality.html) | 报告本地用户的网络质量。 | 4.6.52 |
| [onLastmileProbeResult](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLastmileProbeResult.html) | 报告通话前网络上下行 last mile 质量。 | 4.6.52 |

## 音乐文件播放管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [audioMixingManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/audioMixingManager.html) | 获取伴音管理模块 | 3.9.0 |
| [startAudioMixing](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/startAudioMixing.html) | 开始播放音乐文件 | 3.9.0 |
| [stopAudioMixing](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/stopAudioMixing.html) | 停止播放音乐文件 | 3.9.0 |
| [pauseAudioMixing](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/pauseAudioMixing.html) | 暂停播放音乐文件 | 3.9.0 |
| [resumeAudioMixing](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/resumeAudioMixing.html) | 恢复播放音乐文件 | 3.9.0 |
| [setAudioMixingPlaybackVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/setAudioMixingPlaybackVolume.html) | 设置音乐文件播放音量 | 3.9.0 |
| [setAudioMixingSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/setAudioMixingSendVolume.html) | 设置音乐文件的发送音量 | 3.9.0 |
| [getAudioMixingPlaybackVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/getAudioMixingPlaybackVolume.html) | 获取音乐文件的播放音量 | 3.9.0 |
| [getAudioMixingSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/getAudioMixingSendVolume.html) | 获取音乐文件的发送音量 | 3.9.0 |
| [getAudioMixingDuration](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/getAudioMixingDuration.html) | 获取音乐文件的总长度 | 3.9.0 |
| [setAudioMixingPosition](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/setAudioMixingPosition.html) | 设置音乐文件的播放进度 | 3.9.0 |
| [getAudioMixingCurrentPosition](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/getAudioMixingCurrentPosition.html) | 获取音乐文件当前播放进度 | 3.9.0 |

## 音乐文件播放管理事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [setEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/setEventCallback.html) | 设置伴音事件回调 | 3.9.0 |
| [clearEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingManager/clearEventCallback.html) | 清除伴音事件回调 | 3.9.0 |
| [onAudioMixingStateChanged](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingEventCallback/onAudioMixingStateChanged.html) | 本地用户的音乐文件播放状态改变回调 | 3.9.0 |
| [onAudioMixingTimestampUpdate](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioMixingEventCallback/onAudioMixingTimestampUpdate.html) | 音乐文件播放进度回调 | 3.9.0 |

## 音效文件播放管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [audioEffectManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/audioEffectManager.html) | 获取音效管理模块 | 3.9.0 |
| [getEffectSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/getEffectSendVolume.html) | 获取音效文件播放音量 | 3.9.0 |
| [setEffectSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/setEffectSendVolume.html) | 设置音效文件播放音量 | 3.9.0 |
| [playEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/playEffect.html) | 播放指定音效文件 | 3.9.0 |
| [stopEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/stopEffect.html) | 停止播放指定音效文件 | 3.9.0 |
| [stopAllEffects](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/stopAllEffects.html) | 停止播放所有音效文件 | 3.9.0 |
| [pauseEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/pauseEffect.html) | 暂停音效文件播放 | 3.9.0 |
| [pauseAllEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/pauseAllEffect.html) | 暂停所有音效文件播放 | 3.9.0 |
| [resumeEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/resumeEffect.html) | 恢复播放指定音效文件 | 3.9.0 |
| [resumeAllEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/resumeAllEffect.html) | 恢复播放所有音效文件 | 3.9.0 |
| [setEffectSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/setEffectSendVolume.html) | 设置音效文件的发送音量 | 3.9.0 |
| [getEffectSendVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/getEffectSendVolume.html) | 获取音效文件的发送音量 | 3.9.0 |

## 音效文件播放管理事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [setEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/setEventCallback.html) | 设置音效事件回调 | 3.9.0 |
| [clearEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/clearEventCallback.html) | 清除音效事件回调 | 3.9.0 |
| [onAudioEffectFinished](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectEventCallback/onAudioEffectFinished.html) | 音效结束回调 | 3.9.0 |

## 变声与混响

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setAudioEffectPreset](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setAudioEffectPreset.html) | 设置 SDK 预设的人声的变声音效。 | 4.6.52 |
| [setVoiceBeautifierPreset](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setVoiceBeautifierPreset.html) | 设置 SDK 预设的美声效果。 | 4.6.52 |
| [setLocalVoiceEqualization](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalVoiceEqualization.html) | 设置本地语音音效均衡，即自定义设置本地人声均衡波段的中心频率。 | 4.6.52 |
| [setLocalVoicePitch](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalVoicePitch.html) | 设置本地语音音调。 | 4.6.52 |
| [setLocalVoiceReverbParam](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalVoiceReverbParam.html) | 开启本地语音混响效果。 | 4.6.52 |

## 音量提示

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [enableAudioVolumeIndication](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableAudioVolumeIndication.html) | 启用说话者音量提示 | 3.9.0 |

## 音量提示事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onRemoteAudioVolumeIndication](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onRemoteAudioVolumeIndication.html) | 提示房间内谁正在说话及说话者音量的回调 | 3.9.0 |
| [onLocalAudioVolumeIndication](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLocalAudioVolumeIndication.html) | 本地用户瞬时音量的回调 | 3.9.0 |

## 音频播放路由

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setSpeakerphoneOn](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setSpeakerphoneOn.html) | 设置扬声器是否开启 | 3.9.0 |
| [isSpeakerphoneOn](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isSpeakerphoneOn.html) | 获取扬声器是否开启 | 3.9.0 |

## 耳返

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [enableEarBack](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/enableEarBack.html) | 开启耳返功能 | 3.9.0 |
| [setEarBackVolume](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setEarBackVolume.html) | 设置耳返音量 | 3.9.0 |

## 媒体增强信息 SEI

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [sendSEIMsg](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/sendSEIMsg.html) | 通过主流通道发送媒体补充增强信息。 | 4.6.52 |

## 媒体增强信息 SEI 事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onRecvSEIMsg](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onRecvSEIMsg.html) | 收到远端流的 SEI 内容回调。 | 4.6.52 |

## 旁路推流

方法调用后，在通话中有效。

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [addLiveStreamTask](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/addLiveStreamTask.html) | 添加房间推流任务 | 3.9.0 |
| [updateLiveStreamTask](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/updateLiveStreamTask.html) | 更新修改房间推流任务 | 3.9.0 |
| [removeLiveStreamTask](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/removeLiveStreamTask.html) | 删除房间推流任务 | 3.9.0 |

## 旁路推流事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onLiveStreamState](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLiveStreamState.html) | 直播推流状态回调 | 3.9.0 |

## 跨房间媒体流转发

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [startChannelMediaRelay](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startChannelMediaRelay.html) | 开始跨房间媒体流转发。 | 4.6.52 |
| [updateChannelMediaRelay](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/updateChannelMediaRelay.html) | 更新媒体流转发的目标房间。 | 4.6.52 |
| [stopChannelMediaRelay](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopChannelMediaRelay.html) | 停止跨房间媒体流转发。 | 4.6.52 |

## 跨房间媒体流转发事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onMediaRelayStatesChange](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onMediaRelayStatesChange.html) | 跨房间媒体流转发状态发生改变回调。 | 4.6.52 |
| [onMediaRelayReceiveEvent](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onMediaRelayReceiveEvent.html) | 媒体流相关转发事件回调。 | 4.6.52 |

## 屏幕共享

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [startScreenCapture](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startScreenCapture.html) | 开启屏幕共享 | 3.9.0 |
| [stopScreenCapture](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopScreenCapture.html) | 停止屏幕共享 | 3.9.0 |
| [subscribeRemoteSubStreamVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/subscribeRemoteSubStreamVideo.html) | 订阅或取消订阅远端的屏幕共享辅流视频，订阅之后才能接收远端的辅流视频数据 | 3.9.0 |
| [attachToLocalSubStreamVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToLocalSubStreamVideo.html) | 设置本端的辅流视频回放画布 | 3.9.0 |
| [attachToRemoteSubStreamVideo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcVideoRenderer/attachToRemoteSubStreamVideo.html) | 设置远端的辅流视频回放画布 | 3.9.0 |

## 屏幕共享事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onUserSubStreamVideoStart](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserSubStreamVideoStart.html) | 远端用户开启屏幕共享辅流通道的回调 | 3.9.0 |
| [onUserSubStreamVideoStop](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onUserSubStreamVideoStop.html) | 远端用户停止屏幕共享辅流通道的回调 | 3.9.0 |

## 美颜

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [startBeauty](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startBeauty.html) | 开启美颜功能模块 | 4.6.52 |
| [stopBeauty](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopBeauty.html) | 结束美颜功能模块 | 4.6.52 |
| [enableBeauty](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableBeauty.html) | 暂停或恢复美颜效果 | 4.6.52 |
| [setBeautyEffect](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setBeautyEffect.html) | 设置美颜效果 | 4.6.52 |
| [addBeautyFilter](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/addBeautyFilter.html) | 添加滤镜效果 | 4.6.52 |
| [removeBeautyFilter](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/removeBeautyFilter.html) | 移除滤镜 | 4.6.52 |
| [setBeautyFilterLevel](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setBeautyFilterLevel.html) | 设置滤镜强度 | 4.6.52 |

## 自定义音视频采集与渲染

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setStreamAlignmentProperty](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setStreamAlignmentProperty.html) | 对齐本地系统与服务端的时间 | 4.6.52 |
| [getNtpTimeOffset](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/getNtpTimeOffset.html) | 获取本地系统时间与服务端时间差值 | 4.6.52 |
| [setExternalVideoSource](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setExternalVideoSource.html) | 开启外部视频源数据输入 | 5.4.7 |
| [pushExternalVideoFrame](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/pushExternalVideoFrame.html) | 推送外部视频数据帧 | 5.4.7 |

## 截图

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [takeLocalSnapshot](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/takeLocalSnapshot.html) | 本地视频画面截图。 | 4.6.52 |
| [takeRemoteSnapshot](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/takeRemoteSnapshot.html) | 远端视频画面截图。 | 4.6.52 |

## 截图事件
| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onTakeSnapshotResult](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onTakeSnapshotResult.html) | 截图结果回调 | 4.6.52 |

## 水印

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setLocalVideoWatermarkConfigs](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setLocalVideoWatermarkConfigs.html) | 添加本地视频水印 | 4.6.52 |

## 水印事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onLocalVideoWatermarkState](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onLocalVideoWatermarkState.html) | 水印结果回调 | 4.6.52 |

## 加密

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [enableEncryption](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/enableEncryption.html) | 开启或关闭媒体流加密 | 4.6.52 |

## 客户端音频录制

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [startAudioRecording](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startAudioRecording.html) | 开始客户端录音。 | 4.6.52 |
| [startAudioRecordingWithConfig](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startAudioRecordingWithConfig.html) | 开始客户端录音。 | 4.6.52 |
| [stopAudioRecording](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopAudioRecording.html) | 停止客户端录音。 | 4.6.52 |

## 客户端音频录制事件
| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onAudioRecording](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onAudioRecording.html) | 音频录制状态回调 | 4.6.52 |

## 云代理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [setCloudProxy](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/setCloudProxy.html) | 开启并设置云代理服务 | 4.6.52 |

## 设备管理

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [deviceManager](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/deviceManager.html) | 获取设备管理模块 | 3.9.0 |
| [switchCamera](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/switchCamera.html) | 切换前置/后置摄像头 | 3.9.0 |
| [switchCameraWithPosition](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/switchCameraWithPosition.html) | 指定前置/后置摄像头 | 4.6.52 |
| [setCameraZoomFactor](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setCameraZoomFactor.html) | 设置摄像头缩放比例 | 3.9.0 |
| [getCameraMaxZoom](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/getCameraMaxZoom.html) | 获取摄像头支持的最大视频缩放比例 | 3.9.0 |
| [setCameraTorchOn](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setCameraTorchOn.html) | 设置是否打开闪光灯 | 3.9.0 |
| [setCameraFocusPosition](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setCameraFocusPosition.html) | 设置当前摄像头聚焦点位置 | 3.9.0 |
| [setPlayoutDeviceMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setPlayoutDeviceMute.html) | 设置音频播放设备的状态 | 3.9.0 |
| [isPlayoutDeviceMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isPlayoutDeviceMute.html) | 获取当前音频播放设备是否静音 | 3.9.0 |
| [setRecordDeviceMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setRecordDeviceMute.html) | 设置录音设备的状态 | 3.9.0 |
| [isRecordDeviceMute](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isRecordDeviceMute.html) | 获取当前音频采集设备是否静音 | 3.9.0 |
| [getCurrentCamera](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/getCurrentCamera.html) | 查看当前摄像头配置 | 4.6.52 |
| [isCameraZoomSupported](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isCameraZoomSupported.html) | 检测设备当前使用的摄像头是否支持缩放功能 | 4.6.52 |
| [getCameraCurrentZoom](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/getCameraCurrentZoom.html) | 获取当前缩放比例 | 4.6.52 |
| [isCameraTorchSupported](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isCameraTorchSupported.html) | 检测设备是否支持闪光灯常亮 | 4.6.52 |
| [isCameraFocusSupported](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isCameraFocusSupported.html) | 检测设备是否支持手动对焦功能 | 4.6.52 |
| [isCameraExposurePositionSupported](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/isCameraExposurePositionSupported.html) | 检测设备是否支持手动曝光功能 | 4.6.52 |
| [setCameraExposurePosition](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceManager/setCameraExposurePosition.html) | 设置摄像头的手动曝光位置 | 4.6.52 |

## 设备管理事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [setEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/setEventCallback.html) | 设置设备事件回调 | 3.9.0 |
| [clearEventCallback](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcAudioEffectManager/clearEventCallback.html) | 清除设备事件回调 | 3.9.0 |
| [onAudioDeviceChanged](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceEventCallback/onAudioDeviceChanged.html) | 音频播放设备发生改变 | 3.9.0 |
| [onAudioDeviceStateChange](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceEventCallback/onAudioDeviceStateChange.html) | 音频设备状态切换回调 | 3.9.0 |
| [onVideoDeviceStageChange](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcDeviceEventCallback/onVideoDeviceStageChange.html) | 视频设备状态切换回调 | 3.9.0 |

## 故障排查

| 方法 | 说明 | 起始版本 |
| --- | --- | --- |
| [uploadSdkInfo](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/uploadSdkInfo.html) | 上传 SDK 日志信息 | 3.9.0 |
| [startAudioDump](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/startAudioDump.html) | 开始记录音频 dump | 3.9.0 |
| [stopAudioDump](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcEngine/stopAudioDump.html) | 结束记录音频 dump | 3.9.0 |

## 日志事件

| 事件 | 说明 | 起始版本 |
| --- | --- | --- |
| [onWarning](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onWarning.html) | 发生警告回调 | 3.9.0 |
| [onError](https://doc.yunxin.163.com/nertc/references/flutter/dartdoc/Latest/zh/nertc/NERtcChannelEventCallback/onError.html) | 引擎发生了运行时的错误，需要用户干预 | 3.9.0 |

-->