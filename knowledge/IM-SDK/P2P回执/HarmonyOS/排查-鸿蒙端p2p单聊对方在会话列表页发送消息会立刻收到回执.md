---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: P2P回执
platform: HarmonyOS
title: 鸿蒙端p2p单聊对方在会话列表页发送消息会立刻收到回执
root_cause: 客户代码中监听未关闭导致
solution: 检查并关闭多余的监听器
customers: ["好未来-yach"]
source: chat_history
tags: ["P2P回执","onReceiveP2PMessageReadReceipts","鸿蒙","监听"]
created: 2025-02-13
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙端p2p单聊对方在会话列表页发送消息会立刻收到回执

## 问题详情

**现象**：
鸿蒙端p2p单聊，对方在会话列表页，发送消息会立刻收到onReceiveP2PMessageReadReceipts回执。

## 排查过程

1. 询问是否断点调试过 → 排查调试影响
2. 客户自查发现是有监听没关，是代码问题 → 定位问题

**关键发现**：客户代码中监听未关闭

## 问题原因

客户代码中监听未关闭导致。

## 解决方案

检查并关闭多余的监听器。

## 其他触发场景

