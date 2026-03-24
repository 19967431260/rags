---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话列表
platform: HarmonyOS
title: 鸿蒙会话列表首次进入显示会话ID而非昵称
root_cause: 双方不是好友关系，非好友需要收到对方消息或主动拉取信息才会同步昵称，否则按默认逻辑展示可能显示accid
solution: 调用getUserListFromCloud从服务端获取用户资料，或等待收到对方消息后自动同步
customers: ['成都职工投资集团有限公司']
source: chat_history
tags: ['会话列表', '昵称', 'accid', '非好友', 'getUserListFromCloud']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙会话列表首次进入显示会话ID而非昵称

## 问题详情

**现象**：
第一次进入会话列表页面时显示会话ID，进入会话页面再返回后正常显示会话昵称

## 排查过程



## 问题原因

双方不是好友关系，非好友需要收到对方消息或主动拉取信息才会同步昵称，否则按默认逻辑展示可能显示accid

## 解决方案

调用getUserListFromCloud从服务端获取用户资料，或等待收到对方消息后自动同步

## 其他触发场景

（合并时在此处追加）
