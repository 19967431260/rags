---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组消息
platform: iOS
title: sendTeamMsg返回20000操作失败
root_cause: 客户配置的第三方回调服务返回deny，拒绝该群组消息发送
solution: 检查第三方回调服务的消息审核策略，确认视频消息是否被拦截规则命中
customers: ["VIP云信-广州心晴"]
source: chat_history
tags: ["群组消息", "20000", "操作失败", "第三方回调", "deny"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：iOS sendTeamMsg返回20000操作失败

## 问题详情

**现象**：
iOS端发送群组视频消息时返回错误码20000，提示操作失败。

## 排查过程

1. 获取用户ID 584289 的日志
2. 检查发现第三方回调判定为deny
3. 客户侧回调服务拒绝该消息发送

## 问题原因

客户配置的第三方回调服务返回deny，拒绝该群组消息发送

## 解决方案

检查第三方回调服务的消息审核策略，确认视频消息是否被拦截规则命中

## 其他触发场景
- [iOS] sendTeamMsg返回20000操作失败，来源：['VIP云信-广州心晴']，2026-03-20

