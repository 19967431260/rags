---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成配置
platform: Android
title: AndroidManifest provider authorities冲突
root_cause: AndroidManifest中provider authorities配置与SDK默认配置冲突
solution: 删除android:exported=false行，将provider authorities改为应用自己的包名，删除多余的provider配置
customers: ['江西闪招信息技术有限公司']
source: chat_history
tags: ['AndroidManifest', 'provider', 'authorities', '冲突', '集成']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android AndroidManifest provider authorities冲突

## 问题详情

**现象**：
集成IM UIKit后编译报错，提示AndroidManifest.xml中provider的authorities属性冲突。

## 排查过程

1. 检查AndroidManifest中provider配置
2. 删除android:exported=false行
3. 修改authorities为应用包名
4. 检查是否混用V9和V10版本

## 问题原因

AndroidManifest中provider authorities配置与SDK默认配置冲突

## 解决方案

删除android:exported=false行，将provider authorities改为应用自己的包名，删除多余的provider配置

## 其他触发场景

（合并时在此处追加）
