---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Uniapp
title: IM UIKit Uniapp刷新后会话列表丢失
root_cause: 免费版测试环境无消息漫游功能，Web/H5/Uniapp无本地数据库，每次登录依赖漫游+离线消息生成初始会话。
solution: 1）测试环境可申请开通与正式应用相同的IM版本（有日活限制）；2）生产标准版自带7天消息漫游，刷新后会话可恢复。
customers: ["杭州七夕婚恋服务"]
source: chat_history
tags: ["会话列表", "消息漫游", "Uniapp", "UIKit", "免费版"]
created: 2025-05-28
updated: 2025-03-20
---

## 问题：Uniapp IM UIKit Uniapp刷新后会话列表丢失

## 问题详情

**现象**：
使用IM UIKit V9 Uniapp版本，刷新页面后会话列表消失，无法显示之前的聊天人员信息。当前使用免费版测试环境，AppKey为9b0be02973837fea2968d79886386af6。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Uniapp

## 排查过程

1. 客户询问uni.$UIKitStore?.uiStore?.sessionList能获取多久信息 → 技术支持解释依赖服务器漫游
2. 客户反馈刷新页面会话列表消失 → 技术支持确认免费版无消息漫游功能
3. 客户对比生产环境 → 确认生产标准版有7天消息漫游，刷新后会话可恢复

## 问题原因

免费版测试环境无消息漫游功能，Web/H5/Uniapp无本地数据库，每次登录依赖漫游+离线消息生成初始会话。

## 解决方案

1）测试环境可申请开通与正式应用相同的IM版本（有日活限制）；2）生产标准版自带7天消息漫游，刷新后会话可恢复。

## 其他触发场景

