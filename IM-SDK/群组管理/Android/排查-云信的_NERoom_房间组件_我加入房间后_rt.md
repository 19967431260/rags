---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Android
title: 云信的 NERoom 房间组件，我加入房间后，rt
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 建议基于 neroom 的 sdk 开发
customers: ["VIP云信-海南群云文化（海外）"]
source: chat_history
tags: ["500", "消息", "回调", "视频"]
created: 2024-12-31
updated: 2026-03-20
---

## 问题：Android 云信的 NERoom 房间组件，我加入房间后，rt

## 问题详情

云信的 NERoom 房间组件，我加入房间后，rtc房间的用户不是im的userUuid，好像每次会产生新的rtcUid， D/PassThroughService_K(13024): XKit:notifyEvent method = onPassthrough arguments = {passthroughNotifyData={fromAccid=server_user, body={"sequence":1,"appKey":"58d0841ab9267b6f0d6d54611becb4b1","roomId":9723248,"roomUuid":"1348605925347242

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

建议基于 neroom 的 sdk 开发

## 其他触发场景
