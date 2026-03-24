---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 自定义消息
platform: Uniapp
title: IM自定义消息attach长度限制1024字符
root_cause: 自定义消息attach字段长度限制为1024字符，超出会导致发送失败
solution: 自定义消息attach参数长度限制为1024字符，发送内容需精简控制在限制范围内。
customers: ['云南铁宝机械设备销售有限责任公司']
source: chat_history
tags: ['Uniapp', '自定义消息', 'attach', '长度限制', '414']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp IM自定义消息attach长度限制1024字符

## 问题详情

**现象**：
客户反馈发送自定义消息时，发送人能看到但接收人无反应，调试发现sendCustomMsg failed，code:414。

## 排查过程

1. 客户反馈自定义消息接收方收不到
2. 发送方显示发送失败
3. 查看错误日志发现attach内容过长
4. 确认attach长度超过1024字符限制

## 问题原因

自定义消息attach字段长度限制为1024字符，超出会导致发送失败

## 解决方案

自定义消息attach参数长度限制为1024字符，发送内容需精简控制在限制范围内。

## 其他触发场景

（合并时在此处追加）
