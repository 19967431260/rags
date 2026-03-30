---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS会话免打扰后桌面角标仍显示未读数
root_cause: 云信将账号所有未读数作为角标推送给厂商，免打扰仅影响推送通道不影响未读数统计
solution: iOS端可在切后台时调用registerBadgeCountHandler自定义上报角标数，以当前未读数为基准
customers: ["北京助梦工场-微脉圈"]
source: chat_history
tags: ["iOS", "免打扰", "角标", "badge", "推送"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS会话免打扰后桌面角标仍显示未读数

## 问题详情

**现象**：
客户设置会话免打扰后，APP内未读数显示正确，但桌面图标角标仍包含免打扰会话的消息数量，与微信逻辑不一致。

**环境信息**：
- 平台：iOS

## 排查过程

1. 确认免打扰设置状态
2. 检查角标计算逻辑
3. 确认iOS平台特性

## 根因分析

云信将账号所有未读数作为角标推送给厂商，免打扰仅影响推送通道不影响未读数统计

## 解决方案

iOS端可在切后台时调用registerBadgeCountHandler自定义上报角标数，以当前未读数为基准

## 其他触发场景

（无）
