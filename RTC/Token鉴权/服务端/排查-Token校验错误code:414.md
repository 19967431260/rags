---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: Token鉴权
platform: 服务端
title: Token校验错误code:414
root_cause: Token生成不正确或已过期，导致checksum校验失败。
solution: 检查token生成逻辑，确保使用正确的appkey和appsecret生成token，注意token有效期。
customers: ['FRIENDLINK LIMITED']
source: chat_history
tags: ['RTC', 'Token', '414', 'checksum']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：服务端 Token校验错误code:414

## 问题详情

**现象**：
加入房间时返回{"code":414,"desc":"check checksum error"}错误。

## 排查过程

1. 客户反馈加入房间返回414错误
2. 确认是token校验失败
3. 建议检查token生成逻辑

## 问题原因

Token生成不正确或已过期，导致checksum校验失败。

## 解决方案

检查token生成逻辑，确保使用正确的appkey和appsecret生成token，注意token有效期。

## 其他触发场景

（合并时在此处追加）
