---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息删除
platform: HarmonyOS
title: HarmonyOS deleteMessage只删除本地消息
root_cause: deleteMessage方法的onlyDeleteLocal参数默认为true，仅删除本地消息，不会同步删除云端消息
solution: 将onlyDeleteLocal参数设置为false，并在控制台开启消息单向删除功能
customers: ['南京爱一格']
source: chat_history
tags: ['deleteMessage', '消息删除', 'HarmonyOS', 'onlyDeleteLocal']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：HarmonyOS HarmonyOS deleteMessage只删除本地消息

## 问题详情

**现象**：
客户使用deleteMessage删除消息后，重新拉取历史记录，被删除的消息仍然存在。

## 排查过程

1. 客户提供messageClientId和messageServerId
2. 技术支持检查日志未发现删除请求
3. 确认deleteMessage的第三个参数onlyDeleteLocal默认为true

## 问题原因

deleteMessage方法的onlyDeleteLocal参数默认为true，仅删除本地消息，不会同步删除云端消息

## 解决方案

将onlyDeleteLocal参数设置为false，并在控制台开启消息单向删除功能

## 其他触发场景

（合并时在此处追加）
