---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群成员管理
platform: Flutter
title: removeMembers后群聊消息和会话丢失
root_cause: _isMineLeave方法中踢人通知的判断逻辑有问题，导致群主踢人时误判为自己被踢而删除会话
solution: 修改_isMineLeave方法，将踢人判断改为：通知类型是踢人类型且目标target包含自己时才删除会话。参考GitHub源码：nim-uikit-flutter/nim_conversationkit_ui/lib/view_model/conversation_view_model.dart
customers: ['COOLSHOW PTE.LTD.']
source: chat_history
tags: ['Flutter', 'removeMembers', '群成员', '会话删除', '踢人', '_isMineLeave']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Flutter removeMembers后群聊消息和会话丢失

## 问题详情

**现象**：
调用team.removeMembers接口移除群成员后，当前群聊的聊天信息没有了，首页聊天列表中也没有会话了。

## 排查过程

1. 客户反馈踢人后消息丢失 → 技术支持询问是否调用deleteSession → 客户确认没有主动调用 → 技术支持调试发现收到群通知消息后触发删除会话逻辑 → 定位到_isMineLeave方法判断问题 → 建议修改判断逻辑

## 问题原因

_isMineLeave方法中踢人通知的判断逻辑有问题，导致群主踢人时误判为自己被踢而删除会话

## 解决方案

修改_isMineLeave方法，将踢人判断改为：通知类型是踢人类型且目标target包含自己时才删除会话。参考GitHub源码：nim-uikit-flutter/nim_conversationkit_ui/lib/view_model/conversation_view_model.dart

## 其他触发场景

（合并时在此处追加）
