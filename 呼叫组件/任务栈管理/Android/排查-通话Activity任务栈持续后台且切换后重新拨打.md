---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 任务栈管理
platform: Android
title: 通话Activity任务栈持续后台且切换后重新拨打
root_cause: mainActivity配置了taskAffinity属性，导致通话Activity任务栈与主任务栈分离，通话Activity在后台无法正确finish，切换回任务栈时触发重新拨打
solution: 移除mainActivity的taskAffinity属性配置，避免通话Activity被隔离到独立任务栈
customers: ["一智科技（成都）有限公司"]
source: chat_history
tags: ["taskAffinity","任务栈","startSingleCall","Android","悬浮窗"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：Android 通话Activity任务栈持续后台且切换后重新拨打

## 问题详情

**现象**：
新开的通话Activity任务栈一直持续在后台任务栏，切换到该任务栈后通话会重新拨打出去。客户使用CallKitUI.startSingleCall启动通话。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供视频复现 → 获取复现材料
2. 客户称在mainActivity中加过taskAffinity属性 → 排查方向
3. 客服观察视频认为activity模式像singleInstance → 初步分析
4. 客户确认使用startSingleCall未手动设置singleInstance → 排除显式配置
5. 客服询问taskAffinity使用情况 → 深入排查
6. 客户去掉taskAffinity属性后测试问题解决 → 根因确认

**关键发现**：mainActivity配置了taskAffinity属性，导致通话Activity任务栈与主任务栈分离，通话Activity在后台无法正确finish，切换回任务栈时触发重新拨打

## 问题原因

mainActivity配置了taskAffinity属性，导致通话Activity任务栈与主任务栈分离，通话Activity在后台无法正确finish，切换回任务栈时触发重新拨打。

## 解决方案

移除mainActivity的taskAffinity属性配置，避免通话Activity被隔离到独立任务栈。

## 其他触发场景

（合并时在此处追加）
