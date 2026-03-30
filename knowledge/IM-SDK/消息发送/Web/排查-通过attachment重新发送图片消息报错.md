---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Web
title: 通过attachment重新发送图片消息报错
root_cause: attachment传参方式不支持直接复用已有消息的attachment发送新消息。
solution: 不要使用attachment的传参方式，正常传file对象发送。如需直接传URL发送，建议使用服务器API形式调用，服务器API可以直接传URL，客户端SDK都需要走上传逻辑。
customers: ['云信-宏信动力(北京)科技有限公司']
source: chat_history
tags: ['消息发送', '图片', 'attachment', 'Web']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：Web 通过attachment重新发送图片消息报错

## 问题详情

**现象**：
尝试使用attachment方式重新发送已存在的图片消息时报错。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

attachment传参方式不支持直接复用已有消息的attachment发送新消息。

## 解决方案

不要使用attachment的传参方式，正常传file对象发送。如需直接传URL发送，建议使用服务器API形式调用，服务器API可以直接传URL，客户端SDK都需要走上传逻辑。

## 其他触发场景

（合并时在此处追加：`- [Web] 通过attachment重新发送图片消息报错，来源：['云信-宏信动力(北京)科技有限公司']，2026-03-23`）
