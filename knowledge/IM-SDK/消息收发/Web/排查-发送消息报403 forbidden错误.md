---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Web
title: 发送消息报403 forbidden错误
root_cause: 后台某项配置未开启导致403权限错误
solution: 在控制台检查并开启相关功能配置，确保消息发送权限已启用
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["403", "forbidden", "v2ConversationCreate", "权限配置"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Web 发送消息报403 forbidden错误

## 问题详情

**现象**：
客户使用appkey：ea036dd5ac6c2e1ce691eb9c7bac33e0发送消息时报错403 forbidden，错误详情：v2ConversationCreate命令返回403。试用期内功能正常开启。

## 排查过程

1. 检查appkey试用期状态 → 两个key都在试用期内（2-16到期）
2. 检查发消息功能开关 → 功能正常开启
3. 客户反馈开启后台配置后问题解决

## 问题原因

后台某项配置未开启导致403权限错误

## 解决方案

在控制台检查并开启相关功能配置，确保消息发送权限已启用

## 其他触发场景

（暂无）
