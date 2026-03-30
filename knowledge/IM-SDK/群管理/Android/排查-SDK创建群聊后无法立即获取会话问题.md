---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群管理
platform: Android
title: SDK创建群聊后无法立即获取会话问题
root_cause: 使用SDK方法创建群聊且不邀请其他人时，没有通知消息下发，导致会话列表无法立即显示
solution: 使用UIKit的创建群方法，或在使用SDK创建群后，依赖SDK接口自行插入本地消息。参考文档：https://doc.yunxin.163.com/messaging2/guide/DYzMjA0Njc?platform=client
customers: ['巽风科技']
source: chat_history
tags: ['创建群聊', '会话列表', 'lastMessage', 'UIKit', 'Android']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Android SDK创建群聊后无法立即获取会话问题

## 问题详情

**现象**：
客户使用SDK创建群聊后能获取到会话ID，但创建成功后立即跳转到群聊会话界面发送消息看不到数据，会话列表也找不到该群聊，必须退出重新登录才能看到。

## 排查过程

1. 确认客户使用SDK方法而非UIKit创建群聊
2. 发现客户inviteeAccountIds传入空list创建群聊
3. 确认SDK方法不邀请其他人时没有通知消息下发
4. 建议客户使用UIKit创建群的方法或自行插入本地消息

## 问题原因

使用SDK方法创建群聊且不邀请其他人时，没有通知消息下发，导致会话列表无法立即显示

## 解决方案

使用UIKit的创建群方法，或在使用SDK创建群后，依赖SDK接口自行插入本地消息。参考文档：https://doc.yunxin.163.com/messaging2/guide/DYzMjA0Njc?platform=client

## 其他触发场景

（合并时在此处追加）
