---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 1v1音视频通话
platform: Android
title: 呼叫组件20005错误-currentUserAccId未传
root_cause: 呼叫组件初始化时currentUserAccId未传或传的值与IM登录的accid不一致，导致组件无法获取当前用户账号信息
solution: 呼叫组件初始化时currentUserAccId必须传入IM登录的accid，且createSingleCallParam的A accid也要保持一致，三处accid必须一致
customers: ['VIP云信-陕西建新煤化有限责任公司']
source: chat_history
tags: ['呼叫组件', '20005', 'currentUserAccId', 'hangup', 'Android']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Android 呼叫组件20005错误-currentUserAccId未传

## 问题详情

**现象**：
客户调用音视频功能提示20005错误，日志显示hangup信息为null，currentAccId为null。

## 排查过程

1. 客户反馈调用音视频功能返回20005错误
2. 查看日志发现hangup报错，但前面呼叫信息都为null
3. 技术支持发现组件获取不到currentAccId
4. 确认客户初始化时currentUserAccId参数未正确传入IM登录的accid
5. 客户确认三处accid一致后问题解决

## 问题原因

呼叫组件初始化时currentUserAccId未传或传的值与IM登录的accid不一致，导致组件无法获取当前用户账号信息

## 解决方案

呼叫组件初始化时currentUserAccId必须传入IM登录的accid，且createSingleCallParam的A accid也要保持一致，三处accid必须一致

## 其他触发场景

（合并时在此处追加）
