---
track_type: 排查类
sub_type: SDK问题
product: RTC
feature: 智能纪要
platform: 服务端
title: room name编码处理不当导致创建任务失败的bug
root_cause: room name经过URL编码后在处理时未正确解码，导致服务器无法识别cid；特殊字符（如+）处理异常引发bug
solution: 这是SDK/服务端bug，特殊字符（如+）在URL编码后处理不当导致cid无法识别；后续版本会修复此问题；建议创建房间时避免使用特殊字符
customers: ["生强-dx"]
source: chat_history
tags: ["500错误","room name","URL编码","特殊字符","bug"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：服务端 room name编码处理不当导致创建任务失败的bug

## 问题详情

**现象**：
客户调用task/create接口创建智能纪要任务时报500 Internal Server Error

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：服务端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
500 Internal Server Error

## 排查过程

**关键发现**：room name经过URL编码后在处理时未正确解码，导致服务器无法识别cid

## 问题原因

room name经过URL编码后在处理时未正确解码，导致服务器无法识别cid；特殊字符（如+）处理异常引发bug

## 解决方案

这是SDK/服务端bug，特殊字符（如+）在URL编码后处理不当导致cid无法识别；后续版本会修复此问题；建议创建房间时避免使用特殊字符

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
