---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Android
title: Android冷启动时observeRecentContact不会推送完整会话列表
root_cause: observeRecentContact是会话有变更时触发的监听器，不是用于获取完整会话列表的接口。冷启动时需要主动调用queryRecentContacts查询完整列表。
solution: 冷启动时使用queryRecentContactsBlock主动查询完整会话列表，observeRecentContact仅用于监听会话变更。参考文档：https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android
customers:
- 杭州泰阿网络
source: chat_history
tags:
- Android
- observeRecentContact
- queryRecentContacts
- 会话列表
- 冷启动
created: '2026-01-05'
updated: '2026-03-15'
---

## 问题：Android Android冷启动时observeRecentContact不会推送完整会话列表

## 问题详情

**现象**：
Android端应用冷启动后，observeRecentContact回调只推送部分会话（通常是最新的1条），导致用户反馈大量会话丢失。数据库中有57条会话，但messageObserver只推送了1条，其余56条会话全部丢失。

## 排查过程

1. 检查数据库 → 数据库里有57条会话
2. 检查observeRecentContact回调 → 只推送了1条会话
3. 发现onNewMessage提前填充了allList，导致跳过完整数据库查询

## 问题原因

observeRecentContact是会话有变更时触发的监听器，不是用于获取完整会话列表的接口。冷启动时需要主动调用queryRecentContacts查询完整列表。

## 解决方案

冷启动时使用queryRecentContactsBlock主动查询完整会话列表，observeRecentContact仅用于监听会话变更。参考文档：https://doc.yunxin.163.com/messaging/guide/TgyOTE3MDI?platform=android
