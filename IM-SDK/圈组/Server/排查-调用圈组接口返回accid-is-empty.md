---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 圈组
platform: Server
title: 调用圈组接口返回accid is empty
root_cause: 调用圈组的接口时，服务端没有接收到accid这个入参，是代码传参问题。
solution: 检查代码中accid参数是否正确传入。
customers: ["VIP云信-山东华志汇-StarLink"]
source: chat_history
tags: ["圈组", "414", "accid is empty", "Server"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Server 调用圈组接口返回accid is empty

## 问题详情

**现象**：
V10账号系统调用圈组V9接口返回{"code":414,"desc":"accid is empty"}。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认账号是否注册成功；2. 检查请求参数；3. 检查服务端是否接收到accid入参。

**关键发现**：

## 问题原因

调用圈组的接口时，服务端没有接收到accid这个入参，是代码传参问题。

## 解决方案

检查代码中accid参数是否正确传入。

## 其他触发场景

