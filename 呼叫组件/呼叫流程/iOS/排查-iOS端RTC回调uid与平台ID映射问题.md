---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 呼叫流程
platform: iOS
title: iOS端RTC回调uid与平台ID映射问题
root_cause: 呼叫组件内部生成RTC uid，与IM accid不同。iOS端未设置自定义rtcUid，导致回调中显示的是内部生成的uid。
solution: iOS初始化时通过setupAppKey:withRtcUid:options:方法设置rtcUid参数，传入平台指定的ID。
customers: ['临沂卓创网络科技有限公司']
source: chat_history
tags: ['呼叫组件', 'iOS', 'rtcUid', '回调', 'IM accid']
created: 2025-02-06
updated: 2026-03-23
---

## 问题：iOS iOS端RTC回调uid与平台ID映射问题

## 问题详情

**现象**：
客户使用呼叫组件时，发现RTC事件抄送中的uid是SDK内部生成的，不是客户平台的ID，导致业务逻辑（如金币扣除）无法正常处理。

**环境信息**：
- 平台：iOS
- 产品：呼叫组件

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈通话结束后金币无法扣除 → 查到是uid问题
2. 对比安卓端（正常显示平台ID）与iOS端（显示内部uid）→ 发现差异
3. 确认呼叫组件封装了IM信令和RTC，IM有accid，RTC有uid，两者不同

## 问题原因

呼叫组件内部生成RTC uid，与IM accid不同。iOS端未设置自定义rtcUid，导致回调中显示的是内部生成的uid。

## 解决方案

iOS初始化时通过setupAppKey:withRtcUid:options:方法设置rtcUid参数，传入平台指定的ID。

## 其他触发场景

（合并时在此处追加：`- [iOS] iOS端RTC回调uid与平台ID映射问题，来源：['临沂卓创网络科技有限公司']，2026-03-23`）
