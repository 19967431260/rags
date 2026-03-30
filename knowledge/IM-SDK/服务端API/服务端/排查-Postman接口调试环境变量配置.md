---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 服务端API
platform: 服务端
title: Postman接口调试环境变量配置
root_cause: Postman环境变量需要先创建对应的key，自动计算功能才会生效。
solution: 在Postman环境中创建appKey、secret等参数key（值可先不填），创建后自动计算功能会生效。
customers: ['北京新流通信息科技有限公司']
source: chat_history
tags: ['IM', 'Postman', '环境变量', 'Checksum']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：服务端 Postman接口调试环境变量配置

## 问题详情

**现象**：
客户使用Postman调试接口时，环境变量不会自动计算Checksum等参数。

**环境信息**：
- 平台：服务端
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈Postman环境变量不自动计算 → 检查发现未创建参数key
2. 指导客户创建appKey、secret等key（值可不填）→ 自动计算功能启用

## 问题原因

Postman环境变量需要先创建对应的key，自动计算功能才会生效。

## 解决方案

在Postman环境中创建appKey、secret等参数key（值可先不填），创建后自动计算功能会生效。

## 其他触发场景

（合并时在此处追加：`- [服务端] Postman接口调试环境变量配置，来源：['北京新流通信息科技有限公司']，2026-03-23`）
