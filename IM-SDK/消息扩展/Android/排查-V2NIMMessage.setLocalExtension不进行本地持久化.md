---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息扩展字段
platform: Android
title: V2NIMMessage.setLocalExtension不进行本地持久化
root_cause: setLocalExtension方法仅在消息发送时携带扩展字段到服务器，不做本地数据库持久化。
solution: 使用v2MessageService.updateMessageLocalExtension(updateMessage, "xxx")接口来更新本地消息扩展数据，该接口会同时同步到服务器。参考文档：https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension
customers: ["OCEAN BLUE"]
source: chat_history
tags: ["setLocalExtension", "updateMessageLocalExtension", "V2NIMMessage", "本地持久化", "Android"]
created: 2025-08-10
updated: 2025-08-10
---

## 问题：Android V2NIMMessage.setLocalExtension不进行本地持久化

## 问题详情

**现象**：
客户调用V2NIMMessage的setLocalExtension方法后，发现本地数据没有持久化，重新打开APP数据丢失。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供截图显示V2NIMMessage类没有update方法 → 确认类设计
2. 客服明确setLocalExtension仅用于发送时携带扩展，不做本地存储 → 确认方法用途

**关键发现**：setLocalExtension设计为发送时使用，非本地持久化接口

## 问题原因

setLocalExtension方法仅在消息发送时携带扩展字段到服务器，不做本地数据库持久化。

## 解决方案

使用v2MessageService.updateMessageLocalExtension(updateMessage, "xxx")接口来更新本地消息扩展数据，该接口会同时同步到服务器。参考文档：https://doc.yunxin.163.com/messaging2/client-apis/zIwODM2NTM?platform=client#updateMessageLocalExtension

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
