---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: iOS
title: iOS远端视频画面无法显示
root_cause: 未订阅远端视频流，只绑定画布无法获取视频数据
solution: 调用subscribeRemoteVideo:forUserID:streamType:订阅远端视频流
customers: ["成都华西数字医疗"]
source: chat_history
tags: ["iOS", "RTC", "远端视频", "subscribeRemoteVideo", "画面加载"]
created: 2025-05-07
updated: 2025-03-20
---

## 问题：iOS iOS远端视频画面无法显示

## 问题详情

**现象**：
客户反馈setupRemoteVideoCanvas返回0但远端画面加载不出来。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 确认setupRemoteVideoCanvas只是绑定画布，返回0正常
2. 需要调用subscribeRemoteVideo订阅远端视频流
3. 检查对方是否已加入房间

## 问题原因

未订阅远端视频流，只绑定画布无法获取视频数据

## 解决方案

调用subscribeRemoteVideo:forUserID:streamType:订阅远端视频流

## 其他触发场景

