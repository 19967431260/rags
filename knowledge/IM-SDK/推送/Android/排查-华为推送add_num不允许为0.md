---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: 华为推送add_num不允许为0
root_cause: 华为推送badge的add_num参数取值范围是1-99，不允许设置为0。
solution: 华为推送add_num参数取值范围1-99，如需控制角标显示，建议通过删除证书中的activity配置实现。
customers: ['臻络']
source: chat_history
tags: ['华为推送', 'add_num', '角标', 'HW_PUSH_FAIL']
created: 2025-02-24
updated: 2026-03-23
---

## 问题：Android 华为推送add_num不允许为0

## 问题详情

**现象**：
客户设置华为推送add_num为0后收不到推送，咨询原因。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查推送记录 → 发现HW_PUSH_FAIL
2. 查看错误原因 → Illegal payload, badge add_num value ranges from 1 to 99
3. 确认限制 → 华为推送add_num不允许设置为0

## 问题原因

华为推送badge的add_num参数取值范围是1-99，不允许设置为0。

## 解决方案

华为推送add_num参数取值范围1-99，如需控制角标显示，建议通过删除证书中的activity配置实现。

## 其他触发场景

（合并时在此处追加：`- [Android] 华为推送add_num不允许为0，来源：['臻络']，2026-03-23`）
