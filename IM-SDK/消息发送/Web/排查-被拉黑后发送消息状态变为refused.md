---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Web
title: 被拉黑后发送消息状态变为refused
root_cause: 消息发送后被拉黑，回执失败需要一定时间
solution: 被拉黑后发送消息会返回7101错误码，建议通过try-catch捕获异常，打印ex可以看到"Be pulled black"标识
customers: ['广州欢牛']
source: chat_history
tags: ['拉黑', 'refused', 'sending', '7101', '消息发送']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Web 被拉黑后发送消息状态变为refused

## 问题详情

**现象**：
用户被主播拉黑后发送消息，状态一开始是sending，3分钟后才变成refused，期望立即变为refused。

## 排查过程

1. 查看消息发送接口调用
2. 确认使用v10接口发送消息
3. 测试发现拉黑后会收到7101错误码
4. 建议通过捕获异常判断拉黑状态

## 问题原因

消息发送后被拉黑，回执失败需要一定时间

## 解决方案

被拉黑后发送消息会返回7101错误码，建议通过try-catch捕获异常，打印ex可以看到"Be pulled black"标识

## 其他触发场景

（合并时在此处追加）
