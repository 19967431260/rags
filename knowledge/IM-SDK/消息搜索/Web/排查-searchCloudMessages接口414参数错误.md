---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息搜索
platform: Web
title: searchCloudMessages接口414参数错误
root_cause: sortOrder参数传值有问题
solution: 不传sortOrder参数或检查参数格式，缩小范围排查
customers: ['成都瑞安云科技股份有限公司']
source: chat_history
tags: ['414', 'searchCloudMessages', '参数错误']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Web searchCloudMessages接口414参数错误

## 问题详情

**现象**：
调用searchCloudMessages接口返回414错误，传了四个参数：keyword、beginTime、conversationLimit、sortOrder

## 排查过程



## 问题原因

sortOrder参数传值有问题

## 解决方案

不传sortOrder参数或检查参数格式，缩小范围排查

## 其他触发场景

（合并时在此处追加）
