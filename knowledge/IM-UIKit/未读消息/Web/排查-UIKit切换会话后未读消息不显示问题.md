---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 未读消息
platform: Web
title: UIKit切换会话后未读消息不显示问题
root_cause: 切到其他菜单页时，store层记录的状态还是之前打开的会话，导致该会话产生的消息不记录未读。
solution: 切换菜单时需要告知store层取消当前选中的会话，可调用store.uiStore.selectSession('')方法。
customers: ["广州元沣智能科技有限公司"]
source: chat_history
tags: ["IM-UIKit", "未读消息", "Web", "store", "selectSession"]
created: 2025-06-23
updated: 2025-03-23
---

## 问题：Web UIKit切换会话后未读消息不显示问题

## 问题详情

**现象**：
Web端使用UIKit时，A用户切换到C会话后，B用户发来的消息在A页面不显示未读提示。

## 排查过程

1. 复现问题 → 确认现象
2. 分析原因 → store层记录的状态还是打开的那个会话
3. 尝试解决 → 调用unselectSession
4. 进一步排查 → 建议用selectSession('')

**关键发现**：切到其他菜单页时，store层记录的状态还是之前打开的会话，导致该会话产生的消息不记录未读

## 问题原因

切到其他菜单页时，store层记录的状态还是之前打开的会话，导致该会话产生的消息不记录未读。

## 解决方案

切换菜单时需要告知store层取消当前选中的会话，可调用store.uiStore.selectSession('')方法。

## 其他触发场景

