---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话界面
platform: Android
title: V9 SDK与V10 UIKit混用消息收发问题
root_cause: V10 UIKit仅支持云端会话，V9与V10架构不同不能直接互通
solution: 如果需要互通，统一使用V9；如果不需要互通，创建新应用接V10。V10需要开通云端会话功能。
customers: ['重庆小调', '上海麦糖', '河南仁东']
source: chat_history
tags: ['V9', 'V10', 'UIKit', '云端会话', '混用', '兼容性']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Android V9 SDK与V10 UIKit混用消息收发问题

## 问题详情

**现象**：
客户使用V9云信SDK给V10版本发消息无反应，且UIKit页面点击事件无响应。V10 UIKit只支持云端会话，需要单独开通。

## 排查过程

1. 客户反馈发消息没反应，使用V9 SDK给V10发消息
2. 检查发现客户没有core进程，怀疑初始化问题
3. 确认V10只有一个进程
4. 确认V10 UIKit只支持云端会话，需要单独开通
5. 建议不要混用V9和V10

## 问题原因

V10 UIKit仅支持云端会话，V9与V10架构不同不能直接互通

## 解决方案

如果需要互通，统一使用V9；如果不需要互通，创建新应用接V10。V10需要开通云端会话功能。

## 其他触发场景

（合并时在此处追加）
