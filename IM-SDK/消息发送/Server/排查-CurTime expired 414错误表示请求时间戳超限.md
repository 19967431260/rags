---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Server
title: CurTime expired 414错误表示请求时间戳超限
root_cause: 请求中的CurTime时间戳与云信服务器时间差超过5分钟，导致请求过期被拒绝返回414
solution: 确保请求中传入的CurTime（时间戳）与云信服务器时间差在5分钟以内，否则会返回CurTime is expired 414错误；需校准发起请求机器的系统时间
customers: ["江苏新汇奥信息科技有限公司"]
source: chat_history
tags: ["414","CurTime","时间戳","expired","服务端API"]
created: 2025-08-30
updated: 2026-03-26
---

## 问题：Server CurTime expired 414错误表示请求时间戳超限

## 问题详情

**现象**：
服务端调用接口返回{"code":414,"desc":"CurTime is expired"}，客户询问原因。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供414错误截图 → 获取错误信息
2. 客服确认是CurTime距离服务器时间超过5分钟 → 根因确认
3. 客户了解后确认 → 确认

**关键发现**：请求中的CurTime时间戳与云信服务器时间差超过5分钟，导致请求过期被拒绝返回414

## 问题原因

请求中的CurTime时间戳与云信服务器时间差超过5分钟，导致请求过期被拒绝返回414。

## 解决方案

确保请求中传入的CurTime（时间戳）与云信服务器时间差在5分钟以内，否则会返回CurTime is expired 414错误；需校准发起请求机器的系统时间。

## 其他触发场景

（合并时在此处追加）
