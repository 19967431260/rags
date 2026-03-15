---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 消息撤回
platform: Web
title: Web端撤回消息后对方仍能看到
root_cause: 对方客户端未监听消息撤回通知，无法更新UI
solution: 在客户端监听onMsgRevoked事件，收到撤回通知后更新消息列表UI。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
customers: ["SVIPS云信-北京中科金财科技股份有限公司"]
source: chat_history
tags: ['Web', '消息撤回', 'onMsgRevoked', '消息监听']
created: 2026-02-12
updated: 2026-03-15
---

## 问题：Web Web端撤回消息后对方仍能看到

## 问题详情

**现象**：
Web端撤回消息后，对方客户端仍然能看到消息内容，没有更新为撤回状态。

## 排查过程

1. 检查撤回操作 → 成功
2. 检查对方显示 → 未更新
3. 检查消息监听 → 未监听撤回通知
**关键发现**：未监听消息撤回通知

## 问题原因

对方客户端未监听消息撤回通知，无法更新UI

## 解决方案

在客户端监听onMsgRevoked事件，收到撤回通知后更新消息列表UI。参考文档：https://doc.yunxin.163.com/messaging2/guide/jgyMzYwMzI?platform=web
