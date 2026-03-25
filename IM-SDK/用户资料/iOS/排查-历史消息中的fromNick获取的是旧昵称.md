---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: iOS
title: 历史消息中的fromNick获取的是旧昵称
root_cause: 历史消息的fromNick不会自动更新，需要收到该用户新消息或主动刷新用户资料
solution: 收到消息时会触发用户资料刷新，可参考FAQ了解SDK更新用户资料的时机
customers: ["北京创新一号"]
source: chat_history
tags: ["iOS", "fromNick", "昵称", "用户资料", "历史消息"]
created: 2025-05-09
updated: 2025-03-20
---

## 问题：iOS 历史消息中的fromNick获取的是旧昵称

## 问题详情

**现象**：
通过IMMessage获取fromNick方法返回的是用户以前设置的昵称，而不是最新昵称。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 确认问题现象 → 历史消息显示旧昵称，会话列表显示新昵称
2. 分析更新机制 → V9取的是本地用户资料
3. 确认刷新时机 → 收到消息时会刷新用户资料

## 问题原因

历史消息的fromNick不会自动更新，需要收到该用户新消息或主动刷新用户资料

## 解决方案

收到消息时会触发用户资料刷新，可参考FAQ了解SDK更新用户资料的时机

## 其他触发场景

