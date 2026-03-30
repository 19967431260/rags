---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 本地会话
platform: Web
title: Web端刷新页面后本地会话列表为空
root_cause: 登录时accountId参数类型错误，传了number而非string
solution: 确保登录时accountId传string类型；开启本地会话功能；等待onSyncFinished回调后再获取会话列表
customers: ["广西珍心传媒"]
source: chat_history
tags: ["Web", "本地会话", "getConversationList", "accountId", "数据类型"]
created: 2025-05-20
updated: 2025-03-20
---

## 问题：Web Web端刷新页面后本地会话列表为空

## 问题详情

**现象**：
客户反馈Web端本地会话列表刷新页面后只有空数组，开启漫游消息后仍有问题。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Web

## 排查过程

1. 确认使用V2版本SDK，调用getConversationList接口
2. 检查登录状态和数据同步回调
3. 发现未开启本地会话功能
4. 开启功能后仍有问题，客户提供日志分析
5. 发现登录时accountId传了number类型而非string类型

## 问题原因

登录时accountId参数类型错误，传了number而非string

## 解决方案

确保登录时accountId传string类型；开启本地会话功能；等待onSyncFinished回调后再获取会话列表

## 其他触发场景

