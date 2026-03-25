---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 本地消息
platform: Flutter
title: insertMessageToLocal插入本地消息重新进入后消失
root_cause: 可能是插入参数或获取消息方式问题
solution: 检查insertMessageToLocal是否触发onReceiveMessages回调，getMessageList不传anchorMessage参数
customers: ["VIP云信-武汉梦匠科技有限公司"]
source: chat_history
tags: ["Flutter", "insertMessageToLocal", "本地消息", "V10"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：insertMessageToLocal插入本地消息重新进入后消失

## 问题详情

**现象**：
Flutter端调用insertMessageToLocal插入本地提示消息，插入成功但重新进入聊天界面后消息不见了

**环境信息**：
- 平台：Flutter

## 排查过程

1. 客户反馈insertMessageToLocal插入消息后重新进入消失
2. 检查代码发现使用getMessageList获取历史消息
3. 建议不传anchorMessage参数测试
4. 建议监听onReceiveMessages回调确认插入成功

## 根因分析

可能是插入参数或获取消息方式问题

## 解决方案

检查insertMessageToLocal是否触发onReceiveMessages回调，getMessageList不传anchorMessage参数

## 其他触发场景

（无）
