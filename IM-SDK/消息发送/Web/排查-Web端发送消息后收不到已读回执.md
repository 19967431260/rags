---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 消息发送
platform: Web
title: Web端发送消息后收不到已读回执
root_cause: 初始化SDK时未开启needMsgAck配置
solution: 在初始化SDK时配置needMsgAck: true开启消息回执功能。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
customers: ["SVIPS云信-北京中科金财科技股份有限公司-gj"]
source: chat_history
tags: ['Web', '已读回执', 'needMsgAck', '消息回执']
created: 2026-02-10
updated: 2026-03-15
---

## 问题：Web Web端发送消息后收不到已读回执

## 问题详情

**现象**：
Web端发送消息后，对方已读但收不到已读回执通知。

## 排查过程

1. 检查消息发送 → 成功
2. 检查已读回执 → 未收到
3. 检查SDK配置 → 未开启needMsgAck
**关键发现**：未开启消息回执配置

## 问题原因

初始化SDK时未开启needMsgAck配置

## 解决方案

在初始化SDK时配置needMsgAck: true开启消息回执功能。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
