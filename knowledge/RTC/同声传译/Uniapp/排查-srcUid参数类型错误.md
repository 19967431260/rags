---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 同声传译
platform: Uniapp
title: 同声传译接口参数类型错误
root_cause: srcUid参数类型错误,传入了字符串类型的IM accountId,而该字段要求Number类型的RTC uid
solution: srcUid应传入Number类型的RTC uid(业务侧自定义),而非IM的accountId。uid由业务侧自定义生成,只需确保知道uid对应的用户即可。
customers: ["潍坊华创信息技术有限公司"]
source: chat_history
tags: ["同声传译", "srcUid", "参数类型", "uint64", "RTC uid"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Uniapp 同声传译接口参数类型错误

## 问题详情

**现象**：
调用同声传译接口时报错:request param parser err, json: cannot unmarshal string into Go struct field InterpretParam.data.meeting.simulInterps.srcUid of type uint64。客户将IM的accountId字符串传入了srcUid参数。

## 排查过程

1. 检查请求参数 → 发现srcUid传入了字符串类型的IM accountId

**关键发现**：srcUid应为Number类型的RTC uid,与IM账号无关

## 问题原因

srcUid参数类型错误,传入了字符串类型的IM accountId,而该字段要求Number类型的RTC uid

## 解决方案

srcUid应传入Number类型的RTC uid(业务侧自定义),而非IM的accountId。uid由业务侧自定义生成,只需确保知道uid对应的用户即可。

## 其他触发场景

