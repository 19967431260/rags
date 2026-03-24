---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息扩展字段
platform: 服务端
title: 消息ext扩展字段长度上限及中文计算规则
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 消息ext扩展字段长度上限及中文计算规则

## 问题描述

咨询发送消息接口中ext扩展字段的长度上限，以及中文是否转unicode码的计算方式

## 问题背景

- 当前使用老的专业版套餐
- ext字段默认长度1024，需要更长长度

## 解答

1. **ext字段长度上限**：专业版套餐默认1024字符，最大可调整到10240字符
2. **中文计算规则**：后端通过Java的String.length计算长度，中文算1个字符，不需要转为unicode码
3. **调整方式**：在控制台自助调整字段上限

## 标签

- 服务端
- ext扩展字段
- 长度限制
- 中文编码

## 客户

- FVIP云信-南京麦豆健康

## 会话日期

2025-02-14
