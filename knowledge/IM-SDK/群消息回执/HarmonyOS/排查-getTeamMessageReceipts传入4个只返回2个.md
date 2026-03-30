---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群消息回执
platform: HarmonyOS
title: getTeamMessageReceipts传入4个只返回2个
root_cause: 未返回的消息是因为没有人给它们发过已读回执
solution: 确保消息有被阅读并发送回执
customers: ["好未来-yach"]
source: chat_history
tags: ["getTeamMessageReceipts","群消息回执","已读回执"]
created: 2025-02-25
updated: 2025-03-20
---

## 问题：HarmonyOS getTeamMessageReceipts传入4个只返回2个

## 问题详情

**现象**：
调用getTeamMessageReceipts传入4个消息，只返回了2个，两个message类型是100的没返回。

## 排查过程

1. 分析日志 → 获取日志
2. 确认是那两个消息没有人发过已读回执 → 定位原因

**关键发现**：未返回的消息是因为没有人给它们发过已读回执

## 问题原因

未返回的消息是因为没有人给它们发过已读回执。

## 解决方案

确保消息有被阅读并发送回执。

## 其他触发场景

