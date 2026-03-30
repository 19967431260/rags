本文介绍网易云信音视频呼叫（呼叫组件）的全量 API。

## 概述

网易云信主要提供两套接口，NECallKit 是音视频通话组件的含 UI 接口，NECallEngine API 是音视频通话组件的无 UI 接口，您可以按需使用。

- 使用 NECallKit API，您可以通过简单接口快速实现音视频呼叫，在 App 中添加包括呼叫、接通、拒接、以及通话中音频和视频的开关控制功能，并包含呼叫的 UI 界面。
- 如果 NECallKit 的交互不满足您的需求，您可以使用 NECallEngine API，根据您的业务需求自定义封装。

## NECallKit

API | 描述
--- | ---
getInstance | 创建 NECallKit 实例（单例模式）
init | 初始化接口，需要在功能使用之前，进行初始化
login | 登录接口
logout | 登出接口
call | 拨打通话
accept | 接听通话
hangup | 挂断通话
reject | 拒接
openCamera | 打开摄像头
closeCamera | 关闭摄像头
switchCamera | 切换前置/后置摄像头
openMicrophone | 打开麦克风
closeMicrophone | 关闭麦克风
selectAudioPlaybackDevice | 打开/关闭扬声器
startFloatWindow | 开启悬浮窗
stopFloatWindow | 关闭悬浮窗
setTimeout | 设置超时时间

## NECallEngine

### 接口列表

API | 描述
--- | ---
getInstance | 创建 NECallKit 实例（单例模式）
setup | 初始化接口，需要在功能使用之前，进行初始化
login | 登录接口
logout | 登出接口
call | 拨打通话
accept | 接听通话
hangup | 挂断通话
muteLocalVideo | 打开/关闭摄像头
muteLocalAudio | 打开/关闭麦克风
setSpeakerphoneOn | 打开/关闭扬声器
switchCamera | 切换前置/后置摄像头
setCallConfig | 设置呼叫时的配置参数
getCallConfig | 获取呼叫时的配置参数
hasPermission | 检查权限
getVersion | 获取SDK版本
bringAppToForeground | 将应用从后台返回前台
startFloatWindow | 开启悬浮窗
stopFloatWindow | 关闭悬浮窗
setTimeout | 设置超时时间
on | 添加事件
off | 移除事件

### 事件列表

名称 | 描述
--- | ---
onCallReceived | 接收到通话事件
onCallEnd | 通话结束事件
onCallNotConnected | 通话未建立事件
onFloatWindowClick | 悬浮窗点击事件