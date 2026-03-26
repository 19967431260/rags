---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息管理
platform: 服务端
title: 群组创建返回414 bad custom：custom字段超长
root_cause: 创建群组时传入的custom字段内容超过最大长度1024字符限制
solution: custom字段最大长度为1024字符；精简custom字段内容，或咨询技术支持扩大限制。群组成员上限与custom字段无关。
customers: ["上海金桥"]
source: chat_history
tags: ["群组创建", "414", "custom", "1024"]
created: 2025-07-16
updated: 2025-07-25
---

## 问题：服务端 群组创建返回414 bad custom：custom字段超长

## 问题详情

**现象**：

## 问题原因

创建群组时传入的custom字段内容超过最大长度1024字符限制

## 解决方案

custom字段最大长度为1024字符；精简custom字段内容，或咨询技术支持扩大限制。群组成员上限与custom字段无关。
