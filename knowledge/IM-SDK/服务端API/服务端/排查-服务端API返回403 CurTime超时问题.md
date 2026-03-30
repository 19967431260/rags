---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 服务端API返回403 CurTime超时问题
root_cause: 调用服务端API时，CheckSum计算使用了CurTime（当前时间戳），服务器时间与标准时间偏差过大导致校验失败。
solution: 确保服务器时间与标准时间同步，可使用NTP服务自动同步时间。
customers: ['北京中软融鑫计算机系统工程有限公司']
source: chat_history
tags: ['IM', '服务端API', '403', 'CurTime', '时间同步']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：服务端 服务端API返回403 CurTime超时问题

## 问题详情

**现象**：
客户调用IM服务端API时返回403错误，提示CurTime超时。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈调用接口返回403 → 怀疑CurTime问题
2. 实施同事检查服务器时间 → 发现与标准时间有偏差
3. 同步服务器时间后 → 问题解决

## 问题原因

调用服务端API时，CheckSum计算使用了CurTime（当前时间戳），服务器时间与标准时间偏差过大导致校验失败。

## 解决方案

确保服务器时间与标准时间同步，可使用NTP服务自动同步时间。

## 其他触发场景

（合并时在此处追加：`- [服务端] 服务端API返回403 CurTime超时问题，来源：['北京中软融鑫计算机系统工程有限公司']，2026-03-23`）
