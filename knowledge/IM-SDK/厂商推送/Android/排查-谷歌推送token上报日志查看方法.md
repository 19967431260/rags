---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 厂商推送
platform: Android
title: 谷歌推送token上报日志未打印
root_cause: 国内手机无Google框架无法获取token；谷歌手机实际已正常上报token，客户未正确查看日志
solution: 谷歌推送需要Google框架支持，国内手机无法使用。谷歌手机登录后会自动上报token，日志关键字：commit mix push token:type 8 tokenName googlepush
customers: ["武汉盛游"]
source: chat_history
tags: ["googlepush", "token上报", "Google框架", "mix_push", "Android"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Android 谷歌推送token上报日志未打印

## 问题详情

**现象**：
配置完谷歌推送后，期望看到推送token上报日志，但未打印。国内小米手机因无Google框架显示unsupported，谷歌手机可以接收离线消息但未看到日志打印。

**环境信息**：
- 平台：Android

**相关日志**：
mix_push: local push environment is unsupported

## 排查过程

1. 检查SDK日志 → 国内小米手机显示mix_push: local push environment is unsupported
2. 确认手机环境 → 国内手机无Google框架，无法获取token
3. 使用谷歌手机测试 → 登录后查询日志
4. 后台查询推送记录 → 确认token已上报：commit mix push token:type 8 tokenName googlepush token chOEO9hCRXmUTIY4fbuqgz...

**关键发现**：日志实际已打印，客户未正确查看或过滤日志

## 问题原因

国内手机无Google框架无法获取token；谷歌手机实际已正常上报token，客户未正确查看日志

## 解决方案

谷歌推送需要Google框架支持，国内手机无法使用。谷歌手机登录后会自动上报token，日志关键字：commit mix push token:type 8 tokenName googlepush

## 其他触发场景
