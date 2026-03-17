---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Web
title: Web端获取会话列表和云端会话配置问题
root_cause: 应用未开通云端会话功能,但初始化配置了云端会话相关参数,导致使用云端会话接口失败
solution: 将初始化配置中shouldSyncUnreadCount设为false,使用V2NIMLocalConversationService.getConversationList获取本地会话。云端会话和本地会话区别:云端会话由服务器维护各端一致不受漫游限制;本地会话通过漫游/离线消息在端上聚合生成,Web端每次登录初始会话依赖消息下发。
customers: ["山西云钢智造网络科技"]
source: chat_history
tags: ["会话列表", "云端会话", "本地会话", "Web", "getConversationList"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Web Web端获取会话列表和云端会话配置问题

## 问题详情

**现象**：
Web端使用V2NIMConversationService.getConversationList获取不到会话列表,同时标记已读功能报错。

## 排查过程

1. 检查获取会话列表接口调用 → 使用了云端会话接口但获取不到数据
2. 检查应用配置 → 确认该应用未开通云端会话
3. 修改初始化配置 → 将shouldSyncUnreadCount改为false
4. 改用本地会话接口 → 使用V2NIMLocalConversationService.getConversationList

**关键发现**: 老版本应用默认未开通云端会话,需使用本地会话接口

## 问题原因

应用未开通云端会话功能,但初始化配置了云端会话相关参数,导致使用云端会话接口失败

## 解决方案

将初始化配置中shouldSyncUnreadCount设为false,使用V2NIMLocalConversationService.getConversationList获取本地会话。云端会话和本地会话区别:云端会话由服务器维护各端一致不受漫游限制;本地会话通过漫游/离线消息在端上聚合生成,Web端每次登录初始会话依赖消息下发。

## 其他触发场景

（暂无）
