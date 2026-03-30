---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 回调
platform: 服务端
title: 回调接口HTTP状态码需返回200且格式为JSON
root_cause: 回调接口需要同时满足两个条件：1）HTTP状态码返回200；2）返回内容格式为JSON
solution: 回调接口必须返回HTTP 200状态码，且response body必须是有效的JSON格式
customers: ["生强-dx"]
source: chat_history
tags: ["回调","HTTP 200","JSON","校验失败"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：服务端 回调接口HTTP状态码需返回200且格式为JSON

## 问题详情

**现象**：
客户配置回调接口时提示地址校验失败

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：服务端
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：回调接口需要同时满足两个条件：1）HTTP状态码返回200；2）返回内容格式为JSON

## 问题原因

回调接口需要同时满足两个条件：1）HTTP状态码返回200；2）返回内容格式为JSON

## 解决方案

回调接口必须返回HTTP 200状态码，且response body必须是有效的JSON格式

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
