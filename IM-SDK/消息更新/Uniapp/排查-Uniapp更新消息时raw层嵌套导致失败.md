---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息更新
platform: Uniapp
title: Uniapp更新消息时raw层嵌套导致失败
root_cause: 数据嵌套在raw字段内导致接口无法正确解析
solution: 去掉raw层，直接将数据内容作为value传入
customers: ['海康华安']
source: chat_history
tags: ['更新消息', 'raw', '自定义消息', 'Uniapp']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp Uniapp更新消息时raw层嵌套导致失败

## 问题详情

**现象**：
更新自定义消息时，客户将数据包装在raw字段内导致更新失败。技术支持建议去掉raw层直接传入数据内容。

## 排查过程

1. 客户反馈更新消息报错\n2. 检查传入数据结构：{raw:{type:"1005",...}}\n3. 建议去掉raw层直接传入\n4. 客户尝试后仍报错，技术支持进一步测试\n5. 最终提供正确处理方案

## 问题原因

数据嵌套在raw字段内导致接口无法正确解析

## 解决方案

去掉raw层，直接将数据内容作为value传入

## 其他触发场景

（合并时在此处追加）
