---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: 服务端
title: 聊天室关闭后transient=true的队列元素未被清空
root_cause: 当前聊天室关闭逻辑不会清理队列元素，与transient=true的期望行为不一致
solution: 目前需在关闭聊天室前自行调用API清理队列。产品侧已记录需求，预计年后优化支持关闭房间时清理transient=true的队列元素
customers: ['武汉盛游']
source: chat_history
tags: ['聊天室', '队列', 'transient', 'queueOffer', '服务端']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：服务端 聊天室关闭后transient=true的队列元素未被清空

## 问题详情

**现象**：
客户使用chatroom/queueOffer.action接口添加队列元素时设置transient=true，期望用户离线或退出时自动清理。但关闭聊天室后重启，发现队列未被清空。

## 排查过程

1. 客户反馈房间8980022377关停后队列未清空
2. 客服初步确认关闭聊天室不会清除队列
3. 客户说明场景：关闭房间踢用户时，transient=true的队列元素应被删除
4. 客服确认当前逻辑确实不会清理
5. 建议客户先自行调用API清理，需求反馈产品年后优化

## 问题原因

当前聊天室关闭逻辑不会清理队列元素，与transient=true的期望行为不一致

## 解决方案

目前需在关闭聊天室前自行调用API清理队列。产品侧已记录需求，预计年后优化支持关闭房间时清理transient=true的队列元素

## 其他触发场景

（合并时在此处追加）
