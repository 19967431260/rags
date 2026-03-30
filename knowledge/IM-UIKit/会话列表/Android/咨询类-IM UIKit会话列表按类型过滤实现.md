---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-UIKit
feature: 会话列表
platform: Android
title: IM UIKit会话列表按类型过滤实现
root_cause: UIKit默认会显示所有会话类型（单聊+群聊），需要通过修改数据源来实现按类型过滤。
solution: 1、将conversationkit-ui手动依赖到本地模块；2、给ConversationViewModel添加一个设置会话类型的方法；3、把getConversationList改成getConversationListByOption并按类型过滤；4、在会话变更回调中根据设置类型区分是否通知UI刷新。UI层代码无需修改，只需改动ConversationViewModel数据源。
customers: ['河南欣博教育咨询有限公司']
source: chat_history
tags: ['IM-UIKit', '会话列表', '过滤', 'ConversationViewModel', 'getConversationListByOption']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：IM UIKit会话列表按类型过滤实现

## 问题详情

**现象**：
客户业务上单聊和群聊是完全独立的两个模块，希望在会话列表中只显示特定类型的会话（如只显示单聊或只显示群聊），需要过滤掉不需要显示的会话类型。

## 排查过程



## 问题原因

UIKit默认会显示所有会话类型（单聊+群聊），需要通过修改数据源来实现按类型过滤。

## 解决方案

1、将conversationkit-ui手动依赖到本地模块；2、给ConversationViewModel添加一个设置会话类型的方法；3、把getConversationList改成getConversationListByOption并按类型过滤；4、在会话变更回调中根据设置类型区分是否通知UI刷新。UI层代码无需修改，只需改动ConversationViewModel数据源。

## 其他触发场景

（合并时在此处追加）
