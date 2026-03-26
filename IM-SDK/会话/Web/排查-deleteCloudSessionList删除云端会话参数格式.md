---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话
platform: Web
title: deleteCloudSessionList删除云端会话参数格式
root_cause: 1. 使用了旧版 API 名称 deleteServerSessions；2. to 字段带上了 team- 前缀导致格式错误
solution: 使用 deleteCloudSessionList 方法，sessions 参数传数组格式：[{sessionId: '会话ID', type: 1}]，其中 to 字段不要带 team- 前缀。参考：https://doc.yunxin.163.com/messaging/guide/jc2MDQ3NTI?platform=web
customers: ["成都神鸟互联网医院有限公司"]
source: chat_history
tags: ["deleteCloudSessionList","云端会话","删除会话","会话ID"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：Web deleteCloudSessionList删除云端会话参数格式

## 问题详情

**现象**：
客户使用 deleteServerSessions 接口删除云端会话时报参数格式错误，无法正确删除会话。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认需使用 getServerSessions 获取的会话列表 → 获取方法
2. 确认方法名为 deleteCloudSessionList（而非 deleteServerSessions） → 方法名
3. 参数 to 字段不要带 team- 前缀 → 参数格式
4. sessions 参数需要用数组格式每个元素传两个字段 → 完整格式

**关键发现**：使用了旧版 API 名称 deleteServerSessions；to 字段带上了 team- 前缀导致格式错误

## 问题原因

使用了旧版 API 名称 deleteServerSessions；to 字段带上了 team- 前缀导致格式错误

## 解决方案

使用 deleteCloudSessionList 方法，sessions 参数传数组格式：[{sessionId: '会话ID', type: 1}]，其中 to 字段不要带 team- 前缀。参考：https://doc.yunxin.163.com/messaging/guide/jc2MDQ3NTI?platform=web

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
