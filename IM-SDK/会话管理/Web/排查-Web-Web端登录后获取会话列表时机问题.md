---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Web
title: Web端登录后获取会话列表时机问题
root_cause: 登录成功后数据同步未完成就调用查询接口
solution: 在onDataSync回调中等待同步完成后再查询会话列表：nim.V2NIMLoginService.on('onDataSync', function (type, state, error) {})
customers: ["上海醒魂科技有限公司"]
source: chat_history
tags: ["Web", "会话列表", "getConversationList", "onDataSync"]
created: 2025-11-28
updated: 2026-03-20
---

## 问题：Web Web端登录后获取会话列表时机问题

## 问题详情

**现象**：
客户反馈同一个账号在浏览器2个窗口登录，一个能获取到会话历史，一个获取不到。

**排查过程**：
1. 检查日志发现调用的是查询云端会话接口
2. 发现问题窗口在登录成功后直接调用
3. 建议等待数据同步完成后再查询

## 问题原因

登录成功后数据同步未完成就调用查询接口

## 解决方案

在onDataSync回调中等待同步完成后再查询会话列表：nim.V2NIMLoginService.on('onDataSync', function (type, state, error) {})
