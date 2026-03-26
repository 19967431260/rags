---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: Flutter与Android原生双层初始化导致ClassCastException崩溃
root_cause: Flutter层和Android原生层同时初始化IM SDK，导致初始化参数和状态冲突，引发ClassCastException。Flutter层的SDK初始化内部也是调用原生层实现，不需要双重初始化。
solution: 1. 只在Flutter层进行SDK初始化，不在原生层初始化\n2. 如果必须使用原生层初始化，确保在Flutter层初始化之前不调用任何IM的getService相关API
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["ClassCastException","Flutter","Android","初始化","崩溃"]
created: 2025-08-02
updated: 2026-03-26
---

## 问题：Android Flutter与Android原生双层初始化导致ClassCastException崩溃

## 问题详情

**现象**：
Flutter端集成V10的UI组件，同时接入Android原生库后初始化发生崩溃。错误：java.lang.ClassCastException: com.netease.nimlib.sdk.auth.LoginInfo cannot be cast to java.lang.Void at FLTLoginService.kt:269。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认客户集成方式 → Flutter层和Android原生层都初始化了IM SDK
2. 确认错误原因 → 重复初始化导致类型转换异常
3. 建议去掉原生层初始化 → 只保留Flutter层初始化
4. 问题解决

**关键发现**：Flutter层和Android原生层同时初始化IM SDK，导致初始化参数和状态冲突，引发ClassCastException。Flutter层的SDK初始化内部也是调用原生层实现，不需要双重初始化。

## 问题原因

Flutter层和Android原生层同时初始化IM SDK，导致初始化参数和状态冲突，引发ClassCastException。Flutter层的SDK初始化内部也是调用原生层实现，不需要双重初始化。

## 解决方案

1. 只在Flutter层进行SDK初始化，不在原生层初始化
2. 如果必须使用原生层初始化，确保在Flutter层初始化之前不调用任何IM的getService相关API

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
