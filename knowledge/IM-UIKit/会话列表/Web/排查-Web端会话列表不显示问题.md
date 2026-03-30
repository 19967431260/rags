---
track_type: 排查类
sub_type: 功能配置
product: IM-UIKit
feature: 会话管理
platform: Web
title: Web端会话列表不显示问题
root_cause: Web端没有本地DB，依赖漫游消息，需要开启漫游或云端会话
solution: Web端没有本地DB，依赖漫游消息。需要开启漫游功能，或者使用云端会话(V10新能力)。云端会话需要开通IM高级版，在管理后台开启功能开关，并设置SDKOptions.enableV2CloudConversation = true。
customers: ["郑州开缘商贸有限公司"]
source: chat_history
tags: ["会话列表", "漫游", "云端会话", "Web端"]
created: 2025-05-14
updated: 2025-03-23
---

## 问题：Web Web端会话列表不显示问题

## 问题详情

**现象**：
组件集成后没有发送按钮和输入框，会话列表无法正常显示。

**环境信息**：
- 平台：Web

## 排查过程

**关键发现**：Web端依赖漫游消息或云端会话

## 问题原因

Web端没有本地DB，依赖漫游消息，需要开启漫游或云端会话

## 解决方案

Web端没有本地DB，依赖漫游消息。需要开启漫游功能，或者使用云端会话(V10新能力)。云端会话需要开通IM高级版，在管理后台开启功能开关，并设置SDKOptions.enableV2CloudConversation = true。
