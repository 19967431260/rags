---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息接收
platform: 微信小程序
title: 小程序端登录后onReceiveMessagesModified重复收到更新消息
root_cause: 监听数据同步事件的写法不正确，错误的监听了会话数据同步而非消息同步，导致数据同步完成后仍在重复收到消息更新回调
solution: 使用nim.V2NIMLoginService.on('onDataSync', callback)监听数据同步完成回调：1. 注册回调函数，参数为(V2NIMDataSyncType type, V2NIMDataSyncState state, V2NIMError error) 2. 当type=1（消息数据同步）且state=3（同步完成）时，才代表所有消息数据同步完成 3. 在此之后再注册onReceiveMessagesModified监听，可以避免收到重复的更新通知
customers: ["浙江佰士富信息技术有限公司"]
source: chat_history
tags: ["onReceiveMessagesModified","onDataSync","数据同步","微信小程序","登录","V2NIMLoginService"]
created: 2025-08-26
updated: 2026-03-26
---

## 问题：微信小程序 小程序端登录后onReceiveMessagesModified重复收到更新消息

## 问题详情

**现象**：
小程序端使用V10版本，登录后每次调用服务端API更新消息，之后onReceiveMessagesModified都会被触发，收到已更新过的消息，疑似重复收到通知。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：V10
- 系统版本 / 设备：微信小程序
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户监听的是会话数据同步事件（V2NIMDataSyncType类型），但传入了错误的监听方式 → 定位到监听方式使用错误
2. 客服确认应该监听onDataSync方法，当type=1且state=3时才是所有数据同步完成 → 明确了正确的监听API

**关键发现**：客户错误地监听了会话数据同步而非消息同步，导致数据同步完成后仍在重复收到消息更新回调

## 问题原因

监听数据同步事件的写法不正确，错误的监听了会话数据同步而非消息同步，导致数据同步完成后仍在重复收到消息更新回调

## 解决方案

使用nim.V2NIMLoginService.on('onDataSync', callback)监听数据同步完成回调：
1. 注册回调函数，参数为(V2NIMDataSyncType type, V2NIMDataSyncState state, V2NIMError error)
2. 当type=1（消息数据同步）且state=3（同步完成）时，才代表所有消息数据同步完成
3. 在此之后再注册onReceiveMessagesModified监听，可以避免收到重复的更新通知

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
