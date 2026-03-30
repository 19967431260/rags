---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: iOS
title: 嵌套滑动框架下LocalConversationController不显示会话
root_cause: 登录后未立即跳转至会话列表，导致监听不到数据同步完成事件
solution: 在会话列表的super.viewDidLoad()之前手动设置viewModel.syncFinished = true
customers: ["VIP云信-武汉星辰大海"]
source: chat_history
tags: ["LocalConversationController", "会话列表", "嵌套滑动", "iOS", "UIKit", "syncFinished"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：嵌套滑动框架下LocalConversationController不显示会话

## 问题详情

**现象**：
iOS项目集成第三方嵌套滑动框架后，继承于LocalConversationController的VC放在框架上时本地会话列表不显示，直接放tabbar上可正常加载

**环境信息**：
- 平台：iOS

## 排查过程

1. 客户反馈集成嵌套滑动框架后会话列表不显示
2. 分析发现登录后不是马上跳转到会话列表页面
3. 会话列表页面监听不到数据同步完成事件
4. 建议在viewDidLoad之前手动设置syncFinished

## 根因分析

登录后未立即跳转至会话列表，导致监听不到数据同步完成事件

## 解决方案

在会话列表的super.viewDidLoad()之前手动设置viewModel.syncFinished = true

## 其他触发场景

（无）
