---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Android
title: IM UIKit切换账号后会话列表数据未刷新
root_cause: UIKit会话列表数据未在账号切换时自动清理和重新加载。
solution: 两种解决方案：1）切换账号时重新创建ConversationBaseFragment；2）改造源码，在ConversationViewModel中添加登录状态监听，退出时清理数据，登录成功后重新加载。清空方法：ConversationBaseFragment.conversationView.removeAll()，重新加载：ConversationBaseFragment.viewModel.getConversationData()。
customers: ["江西闪招信息技术有限公司"]
source: chat_history
tags: ["UIKit", "会话列表", "切换账号", "数据刷新", "Android"]
created: 2025-05-08
updated: 2025-03-20
---

## 问题：Android IM UIKit切换账号后会话列表数据未刷新

## 问题详情

**现象**：
使用IM UIKit时，切换账号后会话列表数据未正确刷新，切换到空会话列表账号时界面不更新。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Android

## 排查过程

1. 客户反馈切换账号后会话列表未刷新 → 技术支持提供两种方案
2. 方案一：切换账号时重新创建ConversationBaseFragment
3. 方案二：改造ConversationViewModel，监听登录状态变化清理数据

## 问题原因

UIKit会话列表数据未在账号切换时自动清理和重新加载。

## 解决方案

两种解决方案：1）切换账号时重新创建ConversationBaseFragment；2）改造源码，在ConversationViewModel中添加登录状态监听，退出时清理数据，登录成功后重新加载。清空方法：ConversationBaseFragment.conversationView.removeAll()，重新加载：ConversationBaseFragment.viewModel.getConversationData()。

## 其他触发场景

