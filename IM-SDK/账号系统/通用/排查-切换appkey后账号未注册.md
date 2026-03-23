---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号系统
platform: 通用
title: 切换appkey后账号未注册
root_cause: 切换appkey后，云信侧账号需要重新注册
solution: 切换appkey后需要重新注册云信账号，检查业务服务器注册逻辑。
customers: ["枝江市茹恋贸易有限公司"]
source: chat_history
tags: ["appkey","账号注册","302","切换"]
created: 2025-06-08
updated: 2025-06-08
---

## 问题：通用 切换appkey后账号未注册

## 问题详情

**现象**：
客户换了appkey后iOS登录返回302，Android正常。

## 排查过程

1. 检查账号注册流程 → 检查流程
2. 发现切换appkey后accid未注册 → 发现问题
3. 需要服务端配合注册 → 解决方案

**关键发现**：切换appkey后，云信侧账号需要重新注册

## 问题原因

切换appkey后，云信侧账号需要重新注册

## 解决方案

切换appkey后需要重新注册云信账号，检查业务服务器注册逻辑。

## 其他触发场景

