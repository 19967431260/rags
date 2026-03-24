---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自定义消息
platform: Android
title: 服务端发送自定义消息attachment字段有时为空
root_cause: 接收端未正确注册消息解析器，或注册时机/次数不正确。
solution: 在SDK初始化成功后注册消息解析器，确保全局只注册一次。参考文档：https://doc.yunxin.163.com/messaging/guide/DY3Mjg5NjE
customers: ["初晴/核芯"]
source: chat_history
tags: ["自定义消息", "attachment", "消息解析器", "注册"]
created: 2025-02-24
updated: 2025-03-20
---

## 问题：Android 服务端发送自定义消息attachment字段有时为空

## 问题详情

**现象**：
服务端发送自定义消息，客户端收到的消息有的有attachment字段，有时没有。使用sendMsg.action接口发送type=100的自定义消息。

**环境信息**：
- 平台：Android
- 接口：sendMsg.action
- 消息类型：type=100自定义消息

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析消息差异 → 有attachment的消息注册了消息解析器
2. 问题定位 → 接收端未在初始化成功后注册解析器或注册多次
3. 解决方案 → 参考文档在初始化成功后注册解析器，保证全局只注册一次

**关键发现**：消息解析器注册问题

## 问题原因

接收端未正确注册消息解析器，或注册时机/次数不正确。

## 解决方案

在SDK初始化成功后注册消息解析器，确保全局只注册一次。参考文档：https://doc.yunxin.163.com/messaging/guide/DY3Mjg5NjE

## 其他触发场景
