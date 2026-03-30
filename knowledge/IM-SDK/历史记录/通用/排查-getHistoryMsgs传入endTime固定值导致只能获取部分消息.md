---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史记录
platform: 通用
title: getHistoryMsgs传入endTime固定值导致只能获取部分消息
root_cause: 客户代码中endTime传了固定值，导致只能获取该时间点之前的消息
solution: 检查代码中endTime为什么传了固定值，应传0或不传以获取全部历史记录
customers: ["杭州东方网升"]
source: chat_history
tags: ["getHistoryMsgs", "endTime", "历史记录", "参数错误"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：通用 getHistoryMsgs传入endTime固定值导致只能获取部分消息

## 问题详情

**现象**：
客户侧调用getHistoryMsgs只能获取6条消息，而开发者侧使用相同账号可以获取全部记录。日志显示客户侧endTime传了固定值1769668498596

## 排查过程

1. 对比客户侧和开发者侧日志 → 发现入参差异
2. 检查endTime参数 → 客户侧传固定值1769668498596，开发者侧传1769674342830

**关键发现**：endTime传固定值限制了查询范围

## 问题原因

客户代码中endTime传了固定值，导致只能获取该时间点之前的消息

## 解决方案

检查代码中endTime为什么传了固定值，应传0或不传以获取全部历史记录

## 其他触发场景

（暂无）
