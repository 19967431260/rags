---
track_type: 排查类
sub_type: 使用问题
product: 短信
feature: 模板管理
platform: Server
title: 短信模板403错误authcode sms no authorization
root_cause: 使用的是系统默认的语音验证码模板，普通验证码需要重新创建模板。
solution: 普通验证码短信需要重新创建模板，不能使用系统默认的语音验证码模板。
customers: ['深圳市森愈网络科技有限公司']
source: chat_history
tags: ['短信', '403', '模板', '验证码']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Server 短信模板403错误authcode sms no authorization

## 问题详情

**现象**：
客户测试短信模板时提示403错误：authcode sms no authorization。

**环境信息**：
- 平台：Server
- 产品：短信

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

使用的是系统默认的语音验证码模板，普通验证码需要重新创建模板。

## 解决方案

普通验证码短信需要重新创建模板，不能使用系统默认的语音验证码模板。

## 其他触发场景

（合并时在此处追加：`- [Server] 短信模板403错误authcode sms no authorization，来源：['深圳市森愈网络科技有限公司']，2026-03-23`）
