---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Uniapp
title: sendMessage发送消息报错190001空指针异常
root_cause: 客户直接使用new创建message对象，而非调用消息构建API生成，导致参数缺失。
solution: 使用消息构建API生成消息对象，不要直接new message。
customers: ['武汉极意网络科技有限公司']
source: chat_history
tags: ['190001', 'sendMessage', '空指针', 'Uniapp', '消息构建']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：sendMessage发送消息报错190001空指针异常

## 问题详情

**现象**：
调用sendMessage发送消息时SDK抛出异常：Attempt to invoke virtual method 'int java.lang.Object.hashCode()' on a null object reference，错误码190001。初始化IM和登录成功，创建空会话也成功，但发送消息失败。

## 排查过程

1. 确认问题必现 → 客户反馈一次都发不出去\n2. 检查平台 → 安卓端\n3. 查看日志 → 发现sendMessageParams is null\n4. 客户自行定位 → 消息构建方式错误

## 问题原因

客户直接使用new创建message对象，而非调用消息构建API生成，导致参数缺失。

## 解决方案

使用消息构建API生成消息对象，不要直接new message。

## 其他触发场景

（合并时在此处追加）
