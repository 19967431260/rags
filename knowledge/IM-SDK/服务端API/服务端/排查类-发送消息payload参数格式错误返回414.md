---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 发送消息payload参数格式错误返回414
root_cause: pushPayload参数需要传入JSON格式的字符串，而不是普通字符串或其他格式。
solution: pushPayload参数需要传入JSON格式的字符串，确保参数格式正确。
customers: ['十点开工(广州)网络投资有限公司']
source: chat_history
tags: ['服务端API', 'payload', '414', 'JSON格式', '离线推送']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：发送消息payload参数格式错误返回414

## 问题详情

**现象**：
使用服务端API发送消息时，添加params参数后返回414错误，不加则返回成功。

## 排查过程

1. 客户反馈添加params参数返回414 → 技术支持分析参数格式
2. 确认payload需要是JSON格式字符串 → 指导客户修改参数格式

## 问题原因

pushPayload参数需要传入JSON格式的字符串，而不是普通字符串或其他格式。

## 解决方案

pushPayload参数需要传入JSON格式的字符串，确保参数格式正确。

## 其他触发场景

（合并时在此处追加）
