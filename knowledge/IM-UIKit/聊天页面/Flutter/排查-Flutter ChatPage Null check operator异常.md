---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 聊天页面
platform: Flutter
title: Flutter ChatPage Null check operator异常
root_cause: 待确认，可能与会话初始化或用户数据获取有关
solution: 检查会话ID对应的用户是否存在，确认IM登录成功。如问题持续，提供完整SDK日志进一步分析
customers: ['中科智感（湛江）科技发展有限公司']
source: chat_history
tags: ['Flutter', 'UIKit', 'NullPointer', 'chat_page', '异常']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Flutter Flutter ChatPage Null check operator异常

## 问题详情

**现象**：
客户集成Flutter UIKit(nim_chatkit_ui 9.7.3)后，打开聊天页面出现Null check operator used on a null value异常，报错位置在chat_page.dart:164和chat_kit_message_list.dart:307。

## 排查过程

1. 客户反馈打开会话页面出现空指针异常
2. 技术支持建议检查会话ID对应的用户是否存在
3. 确认登录是否成功
4. 客户确认用户存在且登录成功
5. 需要进一步获取日志分析

## 问题原因

待确认，可能与会话初始化或用户数据获取有关

## 解决方案

检查会话ID对应的用户是否存在，确认IM登录成功。如问题持续，提供完整SDK日志进一步分析

## 其他触发场景

（合并时在此处追加）
