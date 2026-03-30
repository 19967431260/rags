---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 自定义消息
platform: Android
title: V10自定义消息attachment为空的处理方法
root_cause: V10自定义消息需要注册消息解析器（CustomAttachmentParser），SDK收到消息后需通过解析器解析attachment字段后才能获取内容
solution: 需注册自定义消息解析器：实现CustomAttachmentParser接口并在初始化时注册；解析后attachment才有内容；参考文档：doc.yunxin.163.com/messaging-uikit/guide/DAzMTAxMTY?platform=android
customers: ["武汉盛游"]
source: chat_history
tags: ["自定义消息","attachment","V10","CustomAttachmentParser","消息解析器"]
created: 2025-08-25
updated: 2026-03-26
---

## 问题：Android V10自定义消息attachment为空的处理方法

## 问题详情

**现象**：
V10 Android端接收自定义消息时，attachment字段为空，UI也没显示；服务端确认发送了attachment数据。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：V10
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：V10自定义消息需要注册消息解析器（CustomAttachmentParser），SDK收到消息后需通过解析器解析attachment字段后才能获取内容

## 问题原因

V10自定义消息需要注册消息解析器（CustomAttachmentParser），SDK收到消息后需通过解析器解析attachment字段后才能获取内容。

## 解决方案

需注册自定义消息解析器：实现CustomAttachmentParser接口并在初始化时注册；解析后attachment才有内容；参考文档：doc.yunxin.163.com/messaging-uikit/guide/DAzMTAxMTY?platform=android

## 其他触发场景

（合并时在此处追加）
