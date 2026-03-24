---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话置顶
platform: iOS
title: iOS会话置顶代理回调不执行问题
root_cause: onNotifySyncStickTopSessions是多端同步的代理回调，自己本端操作有方法本身的回调，不走代理。
solution: 本端操作置顶/取消置顶时，使用对应方法本身的回调，而非代理回调。代理回调仅用于多端同步场景。
customers: ['北京云动（会小二）']
source: chat_history
tags: ['IM-SDK', '会话置顶', '代理回调', 'iOS', '多端同步']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：iOS iOS会话置顶代理回调不执行问题

## 问题详情

**现象**：
客户设置了chatExtendManager代理并开启setShouldSyncStickTopSessionInfos配置，登录后onNotifySyncStickTopSessions正常回调，但增加/取消置顶时代理函数不回调。

## 排查过程



## 问题原因

onNotifySyncStickTopSessions是多端同步的代理回调，自己本端操作有方法本身的回调，不走代理。

## 解决方案

本端操作置顶/取消置顶时，使用对应方法本身的回调，而非代理回调。代理回调仅用于多端同步场景。

## 其他触发场景

（合并时在此处追加）
