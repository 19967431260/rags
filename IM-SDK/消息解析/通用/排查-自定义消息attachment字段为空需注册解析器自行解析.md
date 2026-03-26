---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息解析
platform: 通用
title: 自定义消息attachment字段为空需注册解析器自行解析
root_cause: 自定义消息的attach内容存储在attachStr字段中，需要客户端注册自定义消息解析器才能正确解析到attachment字段
solution: 自定义消息解析：attachStr字段需要客户端注册MessageNavigator + 解析器来解析内容，解析后才会填充到attachment字段；参考：https://doc.yunxin.163.com/messaging/guide/DY3Mjg5NjE?platform=android
customers: ["数字传递"]
source: chat_history
tags: ["自定义消息","attachment","attachStr","消息解析器"]
created: 2025-08-25
updated: 2026-03-26
---

## 问题：通用 自定义消息attachment字段为空需注册解析器自行解析

## 问题详情

**现象**：
客户端接收到的自定义消息中attachment字段为空，但attachStr有数据。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供接收到的消息截图，attachment空但attachStr有数据 → 确认问题
2. 客服确认：自定义消息需客户端自行注册解析器解析attachStr → 根因确认
3. 提供Android自定义消息解析文档链接 → 解决方案

**关键发现**：自定义消息的attach内容存储在attachStr字段中，需要客户端注册自定义消息解析器才能正确解析到attachment字段

## 问题原因

自定义消息的attach内容存储在attachStr字段中，需要客户端注册自定义消息解析器才能正确解析到attachment字段。

## 解决方案

自定义消息解析：attachStr字段需要客户端注册MessageNavigator + 解析器来解析内容，解析后才会填充到attachment字段；参考：https://doc.yunxin.163.com/messaging/guide/DY3Mjg5NjE?platform=android

## 其他触发场景

（合并时在此处追加）
