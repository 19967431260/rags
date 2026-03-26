---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS推送角标数自动加1配置
root_cause: ""
solution: 参考知识库FAQ：https://faq.yunxin.163.com/#KB0210 iOS IM SDK角标赋值逻辑说明。若APP有IM之外的未读数，需在角标逻辑中做增量累加而非覆盖。
customers: ["陕西金柏河"]
source: chat_history
tags: ["iOS","角标","推送","未读数","FAQ"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：iOS iOS推送角标数自动加1配置

## 问题详情

**现象**：
客户APP存在IM消息之外的未读数，导致直接设置未读总数覆盖了系统自动累加的角标数。客户需要IM消息的推送角标自动+1而非直接赋值。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认问题现象 → 问题理解

**关键发现**：客户APP存在IM消息之外的未读数，需在角标逻辑中做增量累加

## 问题原因


## 解决方案

参考知识库FAQ：https://faq.yunxin.163.com/#KB0210 iOS IM SDK角标赋值逻辑说明。若APP有IM之外的未读数，需在角标逻辑中做增量累加而非覆盖。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
