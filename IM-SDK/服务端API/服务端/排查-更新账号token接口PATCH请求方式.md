---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: 更新账号token接口PATCH请求方式
root_cause: 更新账号token接口需要使用PATCH请求方式，而非POST。
solution: 调用/actions/refresh_token接口更新账号token时，使用PATCH请求方式。
customers: ['北京中软融鑫计算机系统工程有限公司']
source: chat_history
tags: ['IM', '服务端API', 'PATCH', 'token刷新']
created: 2025-02-11
updated: 2026-03-23
---

## 问题：服务端 更新账号token接口PATCH请求方式

## 问题详情

**现象**：
客户调用更新账号token接口时返回错误，不知道应该使用什么HTTP方法。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户使用POST调用/actions/refresh_token接口 → 返回错误
2. 技术支持确认接口需要使用PATCH请求方式 → 客户修改后成功

## 问题原因

更新账号token接口需要使用PATCH请求方式，而非POST。

## 解决方案

调用/actions/refresh_token接口更新账号token时，使用PATCH请求方式。

## 其他触发场景

（合并时在此处追加：`- [服务端] 更新账号token接口PATCH请求方式，来源：['北京中软融鑫计算机系统工程有限公司']，2026-03-23`）
