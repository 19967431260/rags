---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Server
title: 服务端API发送消息含特殊字符时需URL编码
root_cause: 使用application/x-www-form-urlencoded方式发送时，body字段中的特殊字符（%、+）需要URL编码，否则%会被误解析为URL编码前缀，+会被解析为空格
solution: 发送消息前对body字段进行URL编码，服务端支持%+号的URL编码格式
customers: ["台州浩瀚网络"]
source: chat_history
tags: ["sendMsg","URL编码","414","body","特殊字符"]
created: 2025-08-27
updated: 2026-03-26
---

## 问题：Server 服务端API发送消息含特殊字符时需URL编码

## 问题详情

**现象**：
服务端调用sendMsg接口发送消息，消息body中包含%符号时发送失败返回414错误，包含+号时内容被自动清除。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查日志报错 → 确认错误信息
2. 排除第三方工具测试 → 排除工具问题
3. 确认为URL编码问题 → 根因确认

**关键发现**：使用application/x-www-form-urlencoded方式发送时，body字段中的特殊字符（%、+）需要URL编码，否则%会被误解析为URL编码前缀，+会被解析为空格

## 问题原因

使用application/x-www-form-urlencoded方式发送时，body字段中的特殊字符（%、+）需要URL编码，否则%会被误解析为URL编码前缀，+会被解析为空格。

## 解决方案

发送消息前对body字段进行URL编码，服务端支持%+号的URL编码格式。

## 其他触发场景

（合并时在此处追加）
