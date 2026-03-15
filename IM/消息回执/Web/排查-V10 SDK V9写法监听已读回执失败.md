---
track_type: 排查类
sub_type: 使用问题
product: IM
feature: 消息回执
platform: Web
title: V10 SDK V9写法监听已读回执失败
root_cause: 客户从文档复制监听事件名时，使用的不是真实事件名
solution: 使用正确的事件名进行监听。V9写法应使用onMsgReceipts事件。
customers: ['广州欢牛']
source: chat_history
tags: ['V10', 'V9写法', '已读回执', 'onMsgReceipts', '事件监听']
created: 2026-01-21
updated: 2026-03-15
---

## 问题：Web V10 SDK V9写法监听已读回执失败

## 问题详情

Web V10 SDK使用V9写法时，远端监听不到已读回执。本地(V2写法)调用sendP2PMessageReceipt上报已读，远端(V1写法)的onMsgReceipts监听不到。反向则正常。

## 排查过程

1. 检查本地日志确认已读回执发送成功 2. 检查远端日志发现收到同步数据包但未触发回调 3. 客户发现是监听事件名错误

## 问题原因

客户从文档复制监听事件名时，使用的不是真实事件名

## 解决方案

使用正确的事件名进行监听。V9写法应使用onMsgReceipts事件。
