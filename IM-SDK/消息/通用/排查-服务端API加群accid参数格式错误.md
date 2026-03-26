---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: 通用
title: 服务端API加群accid参数格式错误
root_cause: V10服务端API接口参数需要用表单格式（application/x-www-form-urlencoded）传递，而非JSON body。
solution: 调用V10服务端API时，参数使用表单格式传参（application/x-www-form-urlencoded），而非JSON body。V10新接入建议用V10版本。
customers: ["山东数拍"]
source: chat_history
tags: ["加群接口","accid","表单传参","服务端API","V10"]
created: 2025-08-01
updated: 2026-03-26
---

## 问题：通用 服务端API加群accid参数格式错误

## 问题详情

**现象**：
客户调用服务端加群接口时，传参格式错误导致接口调用失败。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户用JSON格式传参 {"accid":"27"}，接口报错 → 传参格式问题
2. 客服指出应用控制台参数格式不对 → 确认正确格式
3. 改用表单格式传参后成功 → 问题解决

**关键发现**：V10服务端API接口参数需要用表单格式（application/x-www-form-urlencoded）传递，而非JSON body。

## 问题原因

V10服务端API接口参数需要用表单格式（application/x-www-form-urlencoded）传递，而非JSON body。

## 解决方案

调用V10服务端API时，参数使用表单格式传参（application/x-www-form-urlencoded），而非JSON body。V10新接入建议用V10版本。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
