---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 会话列表刷新
platform: iOS
title: iOS UIKit demo会话列表不刷新
root_cause: 需要进一步分析日志确认
solution: 建议先确认云端会话开关状态，如问题仍存在需要提供SDK日志进一步分析。
customers: ['FN0F Jumbomax Ventures Limited']
source: chat_history
tags: ['iOS', 'UIKit', '会话列表', '不刷新', 'demo']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：iOS iOS UIKit demo会话列表不刷新

## 问题详情

**现象**：
下载GitHub上的nim-uikit-ios demo运行后，会话列表不更新，别人发消息过来UI组件没有反应，但控制台日志打印了消息接收。

## 排查过程

1. 客户反馈会话列表不刷新 → 技术支持建议切到9.7分支 → 问题仍存在 → 建议提供日志 → 客户认为是demo本身问题 → 技术支持确认漫游消息已开启 → 客户确认已开启但不生效 → 技术支持拉取日志分析

## 问题原因

需要进一步分析日志确认

## 解决方案

建议先确认云端会话开关状态，如问题仍存在需要提供SDK日志进一步分析。

## 其他触发场景

（合并时在此处追加）
