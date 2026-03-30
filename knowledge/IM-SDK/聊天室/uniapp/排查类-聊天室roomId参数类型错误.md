---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: Uniapp
title: 聊天室roomId参数类型错误
root_cause: 聊天室相关接口的roomId参数要求传入string类型，客户传入了number类型导致参数校验失败
solution: 调用聊天室接口时，roomId参数必须传字符串类型（如：9536803314），不能传数字类型
customers: ['东莞市云特信息科技有限公司']
source: chat_history
tags: ['聊天室', 'roomId', '参数类型', 'string', 'Uniapp']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：聊天室roomId参数类型错误

## 问题详情

**现象**：
客户登录聊天室时传入roomId报参数错误，提示param roomId unexpected

## 排查过程

1. 客户反馈roomId参数报错，客服要求打印err.detail查看
2. 发现错误信息：reason: param roomId unexpected, rules要求type为string
3. 判断roomId类型应为string而非number
关键发现：roomId需要传字符串类型

## 问题原因

聊天室相关接口的roomId参数要求传入string类型，客户传入了number类型导致参数校验失败

## 解决方案

调用聊天室接口时，roomId参数必须传字符串类型（如：9536803314），不能传数字类型

## 其他触发场景

（合并时在此处追加）
