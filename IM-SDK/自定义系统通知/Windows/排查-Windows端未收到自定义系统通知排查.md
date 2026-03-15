---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 自定义系统通知
platform: Windows
title: Windows端未收到自定义系统通知排查
root_cause: 经日志分析，客户端已正常收到消息，可能是业务层处理或展示环节的问题。
solution: 通过日志确认SDK层面已正常接收消息，建议检查业务层对自定义系统通知的处理逻辑和UI展示代码。
customers: ["平安银行"]
source: chat_history
tags: ["Windows", "自定义系统通知", "消息", "日志排查"]
created: 2026-01-06
updated: 2026-03-15
---

## 问题：Windows Windows端未收到自定义系统通知排查

## 问题详情

**现象**：
测试环境中PC端（Windows）未收到自定义系统通知消息，需要排查原因。提供了Windows端日志文件。

## 排查过程

1. 收集Windows端日志（三个日志文件打包）
2. 根据accid（lili610）和消息ID查询日志
**关键发现**：客户端在该时间点实际已正常收到这两条自定义系统通知。

## 问题原因

经日志分析，客户端已正常收到消息，可能是业务层处理或展示环节的问题。

## 解决方案

通过日志确认SDK层面已正常接收消息，建议检查业务层对自定义系统通知的处理逻辑和UI展示代码。

## 其他触发场景

（合并时在此处追加）
