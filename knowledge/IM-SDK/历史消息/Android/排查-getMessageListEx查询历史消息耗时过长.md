---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息
platform: Android
title: getMessageListEx查询历史消息耗时过长
root_cause: V10默认会去服务器查可信时间区间，增加网络请求时间
solution: 建议优先查本地onlyQueryLocal，查不到再按默认查询服务器；或等待后续版本优化
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["历史消息", "性能", "getMessageListEx", "Android"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：Android getMessageListEx查询历史消息耗时过长

## 问题详情

**现象**：
Android端使用getMessageListEx查询30条历史消息需要1秒钟，而V9的GetMessagesDynamically只需333ms。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 对比V9和V10接口耗时
2. 分析日志 → 发现查询云端可信时间区间耗时
3. 测试onlyQueryLocal → 速度提升明显
**关键发现**：SDK默认查询云端验证导致耗时增加

**关键发现**：

## 问题原因

V10默认会去服务器查可信时间区间，增加网络请求时间

## 解决方案

建议优先查本地onlyQueryLocal，查不到再按默认查询服务器；或等待后续版本优化

## 其他触发场景

