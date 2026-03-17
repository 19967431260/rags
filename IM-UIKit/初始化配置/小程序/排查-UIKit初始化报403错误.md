---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 初始化配置
platform: 小程序
title: 小程序UIKit初始化报403错误
root_cause: UIKit初始化时默认开启了AI数字人功能，导致403错误
solution: 在UIKit初始化配置中设置 enableAIUser 字段为 false，与其他初始化配置同级
tags: ["403", "enableAIUser", "初始化", "AI数字人", "小程序"]
customers: ["上海复醒网络科技有限公司"]
source: chat_history
created: 2026-02-05
updated: 2026-03-17
---

## 问题：小程序 小程序UIKit初始化报403错误

## 问题详情

**现象**：
小程序集成IM UIKit时，初始化阶段出现403错误。错误与AI数字人功能相关，但项目未引入该功能。

## 排查过程

1. 检查初始化配置 → 发现报错与AI数字人功能相关
2. 分析错误原因 → UIKit默认开启了AI数字人功能
**关键发现**：UIKit初始化时默认开启了AI数字人功能，导致403权限错误

## 问题原因

UIKit初始化时默认开启了AI数字人功能，导致403错误

## 解决方案

在UIKit初始化配置中设置 enableAIUser 字段为 false，与其他初始化配置同级

## 其他触发场景

