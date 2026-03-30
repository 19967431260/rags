---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息已读状态
platform: Android
title: UIKit单聊已读未读状态控制方法差异
root_cause: UIKit单聊已读状态需要通过MessageProperties.setShowP2pMessageStatus控制，SettingRepo.setShowReadStatus仅对群聊生效
solution: 单聊已读状态控制：chatUIConfig.messageProperties = MessageProperties().apply { setShowP2pMessageStatus(false) }；群聊已读状态控制：SettingRepo.setShowReadStatus(false)
customers: ["VIP云信-深圳市九町科技有限公司"]
source: chat_history
tags: ["UIKit", "已读未读状态", "setShowP2pMessageStatus", "SettingRepo", "文档差异"]
created: 2026-02-11
updated: 2026-03-15
---

## 问题：Android UIKit单聊已读未读状态控制方法差异

## 问题详情

**现象**：
使用UIKit 10.9.1版本，想关闭单聊消息的已读未读状态显示。文档提到使用SettingRepo.setShowReadStatus控制，但实际测试该方法对单聊无效，必须使用chatUIConfig.messageProperties.setShowP2pMessageStatus(false)才能生效。

## 排查过程

1. 按文档使用SettingRepo.setShowReadStatus → 单聊已读状态仍显示
2. 查看源码 → 发现判断逻辑中确实有该字段
3. 尝试setShowP2pMessageStatus(false) → 成功关闭单聊已读状态
**关键发现**：单聊和群聊的已读状态控制方法不同，文档与实际有差异

## 问题原因

UIKit单聊已读状态需要通过MessageProperties.setShowP2pMessageStatus控制，SettingRepo.setShowReadStatus仅对群聊生效

## 解决方案

单聊已读状态控制：chatUIConfig.messageProperties = MessageProperties().apply { setShowP2pMessageStatus(false) }；群聊已读状态控制：SettingRepo.setShowReadStatus(false)
