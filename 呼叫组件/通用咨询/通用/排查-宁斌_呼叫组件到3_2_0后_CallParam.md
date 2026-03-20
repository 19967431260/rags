---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 通用咨询
platform: 通用
title: @宁斌 呼叫组件到3.2.0后 CallParam
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: .calledAccId(mAccId) callerAccid不需要传了吗
customers: ["VIP云信-杭州甘之草科技-dx"]
source: chat_history
tags: ["登录", "消息", "云信", "技术支持", "历史会话"]
created: 2025-01-21
updated: 2026-03-20
---

## 问题：通用 @宁斌 呼叫组件到3.2.0后 CallParam

## 问题详情

@宁斌 呼叫组件到3.2.0后 CallParam.Builder()；.callType(2)；.callerAccId(SPUser.getNimAccount())；.calledAccId(mAccId) callerAccid不需要传了吗；这个currentUserAccId也没了 文档上是必要参数

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

.calledAccId(mAccId) callerAccid不需要传了吗

## 其他触发场景
