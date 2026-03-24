---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 账号
platform: 服务端
title: 服务端鉴权失败checksum错误
root_cause: 使用AppKey而非AppSecret计算checksum
solution: checksum需要使用AppSecret计算，不能用AppKey。
customers: ['南阳启程']
source: chat_history
tags: ['鉴权', 'checksum', 'AppSecret', '服务端', '错误']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：服务端鉴权失败checksum错误

## 问题详情

**现象**：
客户调用服务端API时返回鉴权失败，checksum计算错误。

## 排查过程

1. 客户反馈鉴权失败
2. 询问checksum计算方式
3. 发现客户使用AppKey计算，应使用AppSecret

## 问题原因

使用AppKey而非AppSecret计算checksum

## 解决方案

checksum需要使用AppSecret计算，不能用AppKey。

## 其他触发场景

（合并时在此处追加）
