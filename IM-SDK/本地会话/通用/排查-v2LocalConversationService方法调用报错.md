---
track_type: 排查类
sub_type: 版本问题
product: IM-SDK
feature: 本地会话
platform: 通用
title: v2LocalConversationService 方法调用报错
root_cause: v2LocalConversationService 是 IM SDK V10.x 版本之后才支持的接口
solution: v2LocalConversationService 是 IM SDK V10.x 版本之后才支持的接口。如果使用的是 9.x 版本，需要升级到 10.x 版本才能使用此接口。
customers: ["福建达华智显科技有限公司"]
source: chat_history
tags: ["IM", "V2接口", "本地会话", "版本兼容", "SDK升级"]
created: 2025-05-29
updated: 2025-03-23
---

## 问题：通用 v2LocalConversationService 方法调用报错

## 问题详情

**现象**：
用户调用 v2LocalConversationService 方法时报错，提示该方法不存在。

**环境信息**：
- 平台：通用

## 排查过程

**关键发现**：v2LocalConversationService 是 V10.x 版本之后才支持的接口

## 问题原因

v2LocalConversationService 是 IM SDK V10.x 版本之后才支持的接口

## 解决方案

v2LocalConversationService 是 IM SDK V10.x 版本之后才支持的接口。如果使用的是 9.x 版本，需要升级到 10.x 版本才能使用此接口。
