---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话监听
platform: Android
title: Android端会话监听onConversationChanged无限触发
root_cause: 客户代码中clearUnreadCountByIds与onConversationChanged监听形成循环调用
solution: 检查代码逻辑，避免在onConversationChanged回调中调用会触发会话变更的方法（如clearUnreadCountByIds），防止形成循环调用
customers: ['湖南数播']
source: chat_history
tags: ['onConversationChanged', 'clearUnreadCountByIds', '无限触发', '会话监听', '循环调用']
created: 2025-01-04
updated: 2026-03-23
---

## 问题：Android Android端会话监听onConversationChanged无限触发

## 问题详情

**现象**：
Android端会话监听某个会话时，onConversationChanged方法被无限触发。经排查发现是客户代码中clearUnreadCountByIds方法与会话监听形成了循环调用，导致会话状态不断更新。

## 排查过程

1. 客户反馈会话监听onConversationChanged无限触发\n2. 获取日志分析，发现一直在调用clearUnreadCountByIds\n3. 询问客户最近是否有新功能上线\n4. 客户确认新加了系统用户推消息功能后出现该问题\n5. 客户自查发现方法互相调用导致循环

## 问题原因

客户代码中clearUnreadCountByIds与onConversationChanged监听形成循环调用

## 解决方案

检查代码逻辑，避免在onConversationChanged回调中调用会触发会话变更的方法（如clearUnreadCountByIds），防止形成循环调用

## 其他触发场景

（合并时在此处追加）
