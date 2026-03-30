---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: Android
title: vivo市场审核时IM登录报415错误
root_cause: vivo审核网络对云信link地址进行劫持，导致连接失败
solution: 需联系vivo沟通放开网络限制，云信侧无法针对性处理
customers: ['微鲤蘑菇语音']
source: chat_history
tags: ['415', 'vivo', '登录失败', '网络劫持']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：Android vivo市场审核时IM登录报415错误

## 问题详情

**现象**：
应用在vivo市场审核时，审核人员登录IM经常出现415错误，网络连接失败

## 排查过程

1. 历史排查记录 → 2022年曾遇到2次类似问题
2. 分析网络问题 → 发现vivo内部网络对云信link地址进行了劫持

## 问题原因

vivo审核网络对云信link地址进行劫持，导致连接失败

## 解决方案

需联系vivo沟通放开网络限制，云信侧无法针对性处理

## 其他触发场景

（合并时在此处追加）
