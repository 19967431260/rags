---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 依赖管理
platform: Android
title: UIKit集成时androidx.activity版本冲突
root_cause: ""
solution: 打印依赖树查找androidx.activity:activity-ktx:1.8.0的来源,对该依赖进行exclude排除处理。全局强制版本有时无效,需要针对性排除
customers: ["广州市玺诺王信息技术有限公司"]
source: chat_history
tags: ["androidx.activity", "依赖冲突", "UIKit", "exclude", "依赖树"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Android UIKit集成时androidx.activity版本冲突

## 问题详情

**现象**：
使用IM UIKit时出现依赖冲突问题,全局强制指定androidx.activity:activity-ktx:1.8.0版本无效,但使用SDK 34可以正常工作

## 排查过程

1. 尝试全局强制版本 → 无效
2. 检查SDK版本 → SDK 34可以正常工作

**关键发现**：全局强制版本有时无效,需要针对性排除

## 问题原因

依赖冲突导致版本指定失效

## 解决方案

打印依赖树查找androidx.activity:activity-ktx:1.8.0的来源,对该依赖进行exclude排除处理。全局强制版本有时无效,需要针对性排除

## 其他触发场景
