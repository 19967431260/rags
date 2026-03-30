---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Uniapp
title: Uniapp iOS端RTC插件体积过大
root_cause: 
solution: 当前版本已做过一轮优化，不会超过dcloud平台限制，单独打包不会收费
customers: ["加推"]
source: chat_history
tags: ["RTC", "Uniapp", "iOS", "插件体积"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Uniapp iOS端RTC插件体积过大

## 问题详情

**现象**：
Uniapp插件市场下载的RTC插件iOS端体积很大，总共40M的应用中RTC组件占34M

**环境信息**：
- 平台：Uniapp iOS
- 插件来源：dcloud插件市场

## 排查过程

1. 确认插件体积占比情况
2. 了解dcloud平台限制

**关键发现**：RTC组件在40M应用中占34M

## 问题原因

插件体积较大

## 解决方案

当前版本已做过一轮优化，不会超过dcloud平台限制，单独打包不会收费

## 其他触发场景
