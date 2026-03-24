---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息删除
platform: 通用
title: deleteMsgSelf返回403错误
root_cause: 控制台未开通单向删除消息功能，导致接口调用返回403权限错误。
solution: 在网易云信控制台自助开通单向删除消息功能。
customers: ['乐声网络(广州)有限公司']
source: chat_history
tags: ['deleteMsgSelf', '403', '单向删除', '权限错误']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：deleteMsgSelf返回403错误

## 问题详情

**现象**：
调用deleteMsgSelf接口删除消息时返回403错误，回调未执行且消息未删除成功。

## 排查过程

1. 客户反馈删除消息回调未走且未删除成功 → 技术支持查看日志
2. 日志显示deleteMsgSelf返回403 → 确认是功能未开通导致

## 问题原因

控制台未开通单向删除消息功能，导致接口调用返回403权限错误。

## 解决方案

在网易云信控制台自助开通单向删除消息功能。

## 其他触发场景

（合并时在此处追加）
