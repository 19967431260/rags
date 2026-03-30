---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: iOS
title: iOS发送消息时自定义apnsPayload字段无效
root_cause: 使用了已废弃的V1消息对象，V1版本的apnsPayload等字段已不再生效。
solution: 升级到V2 NIM SDK，使用V2NIMMessage对象发送消息，并正确设置pushPayload字段。
customers:
- 上海文攸网络科技有限公司_芜湖市乖巧虎科技有限公司
source: chat_history
tags:
- iOS
- apnsPayload
- 离线推送
- V2
created: '2026-01-06'
updated: '2026-03-15'
---

## 问题：iOS iOS发送消息时自定义apnsPayload字段无效

## 问题详情

**现象**：
iOS端发送消息时设置了apnsPayload字段，但接收方收到的离线推送内容仍然是默认内容，自定义推送内容未生效。

## 排查过程



## 问题原因

使用了已废弃的V1消息对象，V1版本的apnsPayload等字段已不再生效。

## 解决方案

升级到V2 NIM SDK，使用V2NIMMessage对象发送消息，并正确设置pushPayload字段。
