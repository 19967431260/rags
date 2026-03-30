---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 未读数清零
platform: Uniapp
title: markConversationRead后unreadCount未更新
root_cause: markConversationRead调用后登出导致请求未发出
solution: 使用clearUnreadCountByIds方法清理未读数，避免在页面退出时执行相关操作。
customers: ['四川白宇信息科技有限公司']
source: chat_history
tags: ['Uniapp', '未读数', 'markConversationRead', 'clearUnreadCountByIds', 'logout']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：Uniapp markConversationRead后unreadCount未更新

## 问题详情

**现象**：
调用markConversationRead标记会话已读后，再次获取会话详情unreadCount没有改变。

## 排查过程

1. 客户反馈未读数未清零 → 技术支持查看日志发现调用了logout → 建议不登出再试 → 客户确认未登出 → 分析日志发现请求未发出 → 建议使用clearUnreadCountByIds

## 问题原因

markConversationRead调用后登出导致请求未发出

## 解决方案

使用clearUnreadCountByIds方法清理未读数，避免在页面退出时执行相关操作。

## 其他触发场景

（合并时在此处追加）
