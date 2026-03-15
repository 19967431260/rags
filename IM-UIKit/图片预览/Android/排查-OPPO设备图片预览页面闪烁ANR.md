---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 图片预览
platform: Android
title: OPPO设备图片预览页面闪烁ANR
root_cause: Application和BaseActivity中都有语言切换代码,导致Activity反复重建
solution: 修改WatchImageActivity基类为BaseActivity,避免语言切换冲突;或在WatchImageActivity的AndroidManifest配置中添加android:configChanges="orientation|keyboardHidden|screenSize|smallestScreenSize"
customers: ["乐次元"]
source: chat_history
tags: ["WatchImageActivity", "ANR", "闪烁", "语言切换", "OPPO", "Android"]
created: 2026-02-26
updated: 2026-03-15
---

## 问题：Android OPPO设备图片预览页面闪烁ANR

## 问题详情

**现象**：
OPPO设备(PEEM00、PEXM00)上打开私信图片时WatchImageActivity页面一直闪烁卡住,出现ANR。客户端在Application和BaseActivity中都有语言切换代码,导致页面反复重建。

**环境信息**：
- 设备：OPPO PEEM00、PEXM00

**相关日志**：
logcat日志显示ANR

## 排查过程

1. 抓取logcat日志 → 发现ANR
2. 检查WatchImageActivity启动次数 → 页面反复创建
3. 检查基类配置 → 发现语言切换逻辑在Application和BaseActivity中重复设置

**关键发现**：WatchImageActivity继承的基类中有语言切换代码,与Application中的语言设置冲突,导致页面反复重建

## 问题原因

Application和BaseActivity中都有语言切换代码,导致Activity反复重建

## 解决方案

修改WatchImageActivity基类为BaseActivity,避免语言切换冲突;或在WatchImageActivity的AndroidManifest配置中添加android:configChanges="orientation|keyboardHidden|screenSize|smallestScreenSize"

## 其他触发场景
