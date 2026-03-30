---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话切换
platform: Web
title: V9 UIKit切换会话方法
root_cause: V9和V10的会话ID拼接方式不同，客户混淆了版本接口。
solution: V9版本点对点session对象拼接方式是p2p-accid，群组是team-tid。
customers: ['杭州泥鳅信息技术有限公司']
source: chat_history
tags: ['IM-UIKit', 'V9', '切换会话', 'conversationId', 'p2p', 'team']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：V9 UIKit切换会话方法

## 问题详情

**现象**：
客户使用V9 SDK但使用V10的接口方式切换会话导致失败。

## 排查过程

1. 客户反馈页面没有切换到指定用户
2. 检查发现客户使用V9 SDK但使用V10的接口和conversationId拼接方式
3. V9点对点session拼接方式是p2p-accid，群组是team-tid
4. 提供V9文档链接

## 问题原因

V9和V10的会话ID拼接方式不同，客户混淆了版本接口。

## 解决方案

V9版本点对点session对象拼接方式是p2p-accid，群组是team-tid。

## 其他触发场景

（合并时在此处追加）
