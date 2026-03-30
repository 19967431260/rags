---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 群组
platform: iOS
title: iOS群已读回执参数错误
root_cause: 控制台未开启群已读回执功能
solution: 先在控制台开启群已读回执功能，再检查入参是否正确
customers: ['积木成林']
source: chat_history
tags: ['群已读回执', 'teamReceiptEnabled', 'iOS', '功能开关']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：iOS iOS群已读回执参数错误

## 问题详情

**现象**：
客户反馈群消息发送时设置teamReceiptEnabled为true，对方收到群消息后发送群已读回执报错。

## 排查过程

1. 客户反馈群已读回执发送报错
2. 经查询该appkey(68012b519bb86aaac8d491130826d303)尚未开启群已读回执功能
**关键发现**：控制台未开启群已读回执功能导致

## 问题原因

控制台未开启群已读回执功能

## 解决方案

先在控制台开启群已读回执功能，再检查入参是否正确

## 其他触发场景

（合并时在此处追加）
