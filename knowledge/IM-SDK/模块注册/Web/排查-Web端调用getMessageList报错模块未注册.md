---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 模块注册
platform: Web
title: Web端调用getMessageList报错模块未注册
root_cause: ESM引入时需要手动注册所需模块
solution: 在初始化时注册对应的模块：V2NIMConversationService、V2NIMMessageService、V2NIMStorageService、V2NIMUserService等。
customers: ['Eagle']
source: chat_history
tags: ['Web', 'V10', '模块注册', 'esm', 'getMessageList']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Web Web端调用getMessageList报错模块未注册

## 问题详情

**现象**：
Web前端调用nim.V2NIMMessageService.getMessageList时提示模块未注册的错误。

## 排查过程

1. 客户反馈接口报错 → 技术支持询问是否esm引入 → 确认是esm引入 → 建议检查模块注册 → 需要注册V2NIMConversationService、V2NIMMessageService等模块

## 问题原因

ESM引入时需要手动注册所需模块

## 解决方案

在初始化时注册对应的模块：V2NIMConversationService、V2NIMMessageService、V2NIMStorageService、V2NIMUserService等。

## 其他触发场景

（合并时在此处追加）
