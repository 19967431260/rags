---
track_type: 排查类
sub_type: 使用问题
product: 智能体
feature: Function Call
platform: 通用
title: 豆包模型Function Call误触发问题
root_cause: Doubao-1.5-lite-32k-250115模型的Function Call识别准确度不足。
solution: 建议使用Doubao-1.5-pro-32k-250115模型替代lite版本，pro版本的识别准确度更好。后续计划引入豆包1.6版本，新版本会有进一步提升。
customers: ["千悟"]
source: chat_history
tags: ["Function Call","豆包","Doubao","误触发","智能体"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：通用 豆包模型Function Call误触发问题

## 问题详情

**现象**：
使用Doubao-1.5-lite-32k-250115模型时，Function Call误触发严重，例如询问"太阳系有多大"会触发查询天气的函数调用。

## 问题原因

Doubao-1.5-lite-32k-250115模型的Function Call识别准确度不足。

## 解决方案

建议使用Doubao-1.5-pro-32k-250115模型替代lite版本，pro版本的识别准确度更好。后续计划引入豆包1.6版本，新版本会有进一步提升。

## 其他触发场景

