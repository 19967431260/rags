---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 动态Token
platform: 通用
title: appkey blocked错误
root_cause: 后台配置了动态token，但客户端没有使用动态token方式登录。
solution: 确认后台配置了动态token后，需要使用动态token方式进行登录。
customers: ["北京集藏科技有限公司"]
source: chat_history
tags: ["appkey blocked", "101403", "动态token", "登录"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：通用 appkey blocked错误

## 问题详情

**现象**：
客户登录时返回appkey blocked错误，code: 101403。

## 排查过程

1. 客户反馈登录返回appkey blocked
2. 检查发现后台配置的是动态token
3. 确认是否使用了动态token登录

## 问题原因

后台配置了动态token，但客户端没有使用动态token方式登录。

## 解决方案

确认后台配置了动态token后，需要使用动态token方式进行登录。

## 其他触发场景
- [通用] appkey blocked错误，来源：['北京集藏科技有限公司']，2026-03-20
- [通用] appkey blocked错误，来源：['北京集藏科技有限公司']，2026-03-20

