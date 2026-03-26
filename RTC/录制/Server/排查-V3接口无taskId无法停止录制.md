---
track_type: 排查类
sub_type: 接口用法咨询
product: RTC
feature: 录制
platform: Server
title: V3接口无taskId无法停止录制
root_cause: 客户在创建录制任务时未保存返回的 taskId，导致停止时无法传入
solution: 调用停止房间录制接口时必须传入 taskId 参数，该参数在创建录制任务成功后会返回。建议在创建录制任务时就保存好 taskId。
customers: ["河北元造宙"]
source: chat_history
tags: ["taskId","停止录制","param error","V3接口","录制任务ID"]
created: 2025-08-29
updated: 2026-03-26
---

## 问题：Server V3接口无taskId无法停止录制

## 问题详情

**现象**：
客户调用 V3 接口停止房间录制时一直报错：{"code":400,"errmsg":"param error: invalid empty taskId"}。客户发现自己没有保存录制任务 ID。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认 V3 接口停止录制时必须传入 taskId → 接口要求确认

**关键发现**：客户在创建录制任务时未保存返回的 taskId，导致停止时无法传入

## 问题原因

客户在创建录制任务时未保存返回的 taskId，导致停止时无法传入

## 解决方案

调用停止房间录制接口时必须传入 taskId 参数，该参数在创建录制任务成功后会返回。建议在创建录制任务时就保存好 taskId。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
