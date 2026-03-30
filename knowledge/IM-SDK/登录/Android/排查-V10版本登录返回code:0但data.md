---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: V10版本登录返回code:0但data为null
root_cause: 登录实际已成功，客户对登录接口返回理解有误
solution: 日志中显示登录返回200和success，建议过滤关键字V2NIMLoginService和login success确认登录状态
customers: ['北京新守心城']
source: chat_history
tags: ['登录', 'V10', 'code:0', 'Android', '多设备']
created: 2025-09-05
updated: 2026-03-25
---

## 问题：Android V10版本登录返回code:0但data为null

## 问题详情

**现象**：
客户反馈IM V10版本登录接口返回{code: 0, data: null, msg: null}，但无法确定是否登录成功。用户有多个设备同时登录(安卓和pad，pad使用自定义设备类型100)。

## 解决方案

日志中显示登录返回200和success，建议过滤关键字V2NIMLoginService和login success确认登录状态
