---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自定义消息
platform: Uniapp
title: V10接口发送消息V9SDK收不到messageType
root_cause: V10服务端接口与V9 SDK不兼容。
solution: V10的服务端接口，1.5.0是V9的SDK，建议用V9的发送消息接口。
customers: ['海南拉米网络科技有限公司']
source: chat_history
tags: ['自定义消息', 'V10', 'V9', 'messageType', 'Uniapp']
created: 2025-02-24
updated: 2026-03-23
---

## 问题：Uniapp V10接口发送消息V9SDK收不到messageType

## 问题详情

**现象**：
后端使用V10接口批量推送自定义消息，前端V9 SDK(1.5.0)收到的消息体没有messageType和subType字段。

**环境信息**：
- 平台：Uniapp
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

V10服务端接口与V9 SDK不兼容。

## 解决方案

V10的服务端接口，1.5.0是V9的SDK，建议用V9的发送消息接口。

## 其他触发场景

（合并时在此处追加：`- [Uniapp] V10接口发送消息V9SDK收不到messageType，来源：['海南拉米网络科技有限公司']，2026-03-23`）
