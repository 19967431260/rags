---
track_type: 排查类
sub_type: 使用问题
product: 其他
feature: 通用
platform: Server
title: 图片审核回调未收到-未传callbackUrl
root_cause: 请求入参中未传入callbackUrl字段
solution: 在发起图片审核请求时，确保上传callbackUrl字段以接收异步回调
customers: ['微鲤科技']
source: chat_history
tags: ['图片审核', '异步回调', 'callbackUrl', '反垃圾']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：服务端 图片审核回调未收到-未传callbackUrl

## 问题详情

**现象**：
客户使用异步图片审核，状态显示等待回调，但未收到回调通知。原因是入参中没有传callbackUrl字段。

## 排查过程

1. 客户反馈等待回调状态 → 客服询问回调方式（推送/轮询）
2. 客户提供taskid → 检查发现入参中没有callbackurl字段

## 问题原因

请求入参中未传入callbackUrl字段

## 解决方案

在发起图片审核请求时，确保上传callbackUrl字段以接收异步回调

## 其他触发场景

（合并时在此处追加）
