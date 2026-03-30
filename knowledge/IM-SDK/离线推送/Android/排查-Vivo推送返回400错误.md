---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: Vivo推送返回400错误
root_cause: vivoField字段传值格式错误，classification应传数字1而非字符串"IM"
solution: 修改vivoField格式为："vivoField":"{\"classification\":1,\"category\":\"IM\"}"
customers: ['北京创新一号']
source: chat_history
tags: ['Vivo推送', '400错误', 'vivoField', 'classification', '推送失败']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android Vivo推送返回400错误

## 问题详情

**现象**：
客户反馈Vivo设备收不到推送，服务端返回HttpCode=400错误。

## 排查过程

1. 检查推送日志 → 发现Vivo推送返回400错误
2. 检查payload参数 → 发现vivoField传值格式不正确
3. 关键发现：vivoField中classification字段传字符串"IM"不正确

## 问题原因

vivoField字段传值格式错误，classification应传数字1而非字符串"IM"

## 解决方案

修改vivoField格式为："vivoField":"{\"classification\":1,\"category\":\"IM\"}"

## 其他触发场景

（合并时在此处追加）
