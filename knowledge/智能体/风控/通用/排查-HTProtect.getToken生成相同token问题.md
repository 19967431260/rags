---
track_type: 排查类
sub_type: 使用问题
product: 智能体
feature: 风控
platform: 通用
title: HTProtect.getToken生成相同token问题
root_cause: 可能是token被二次利用
solution: 检查token获取流程，确保每次重新获取
customers: ["创业系"]
source: chat_history
tags: ["智能体", "风控", "HTProtect", "token"]
created: 2025-05-07
updated: 2025-03-20
---

## 问题：通用 HTProtect.getToken生成相同token问题

## 问题详情

**现象**：
客户反馈风控token生成相同值，咨询什么情况下会一致。

## 排查过程

**关键发现**：可能是token被二次利用

## 问题原因

可能是token被二次利用

## 解决方案

检查token获取流程，确保每次重新获取
