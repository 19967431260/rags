---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 机器人Webhook
platform: Server
title: 机器人消息Webhook收不到回调
root_cause: robotConfigure配置中function字段设置为null导致Webhook无法正常接收回调，应设置为机器人账号ID或直接去掉该字段。
solution: 配置robotConfigure时，function字段应设置为机器人账号ID（如："function": "17354175160"）或直接去掉该字段，不能设置为null。
customers: ['上海力洋软件科技有限公司']
source: chat_history
tags: ['机器人', 'Webhook', '回调', 'robotConfigure', 'function']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：机器人消息Webhook收不到回调

## 问题详情

**现象**：
客户配置机器人Webhook后，给机器人发消息但收不到回调。经排查是robotConfigure配置中function字段设置不正确。

## 排查过程

1. 客户反馈Webhook收不到回调 → 客服检查控制台日志
2. 发现应用套餐已到期，机器人服务被关闭 → 延期试用
3. 再次测试仍无回调 → 检查robotConfigure配置
4. 发现function字段值为null → 修改为与机器人账号一致或去掉该字段
5. 测试成功收到回调

## 问题原因

robotConfigure配置中function字段设置为null导致Webhook无法正常接收回调，应设置为机器人账号ID或直接去掉该字段。

## 解决方案

配置robotConfigure时，function字段应设置为机器人账号ID（如："function": "17354175160"）或直接去掉该字段，不能设置为null。

## 其他触发场景

（合并时在此处追加）
