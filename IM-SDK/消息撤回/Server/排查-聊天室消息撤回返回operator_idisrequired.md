---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息撤回
platform: Server
title: 聊天室消息撤回返回operator_id is required
root_cause: 可能是请求方法或参数格式不正确
solution: 使用DELETE方法调用接口，将参数放在URL中，body设置为null
customers: ["四川白宇信息科技有限公司"]
source: chat_history
tags: ["聊天室", "消息撤回", "414", "operator_id"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：聊天室消息撤回返回operator_id is required

## 问题详情

**现象**：
调用聊天室消息撤回接口返回414错误，提示operator_id is required，但请求中已包含该参数

**环境信息**：
- 平台：Server

## 排查过程

1. 检查operator_id参数 → 发现传的是大写\n2. 提示accid需要小写 → 客户尝试后仍报错\n3. 建议对照参考代码，使用DELETE方法，body为null

## 根因分析

可能是请求方法或参数格式不正确

## 解决方案

使用DELETE方法调用接口，将参数放在URL中，body设置为null

## 其他触发场景

（无）
