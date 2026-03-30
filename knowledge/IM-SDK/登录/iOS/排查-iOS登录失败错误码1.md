---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: iOS
title: iOS登录失败错误码1
root_cause: token无效
solution: 无效token，需要检查入参中的token是否正确
customers: ["VIP_云信-杭州泰阿网络"]
source: chat_history
tags: ["iOS","登录","错误码","invalid token"]
created: 2025-08-06
updated: 2026-03-26
---

## 问题：iOS iOS登录失败错误码1

## 问题详情

**现象**：
客户反馈iOS登录failed error = Error Domain=NIMLocalErrorDomain Code=1 错误的参数

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服要求提供日志排查 → 最终确认是invalid token，无效token

**关键发现**：token无效

## 问题原因

token无效

## 解决方案

无效token，需要检查入参中的token是否正确

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
