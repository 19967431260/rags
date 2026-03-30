---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 图片选择
platform: Android
title: IM UIKit Android 14图片权限适配
root_cause: Android 14部分照片授权后需要额外处理READ_MEDIA_VISUAL_USER_SELECTED权限
solution: 在权限请求结果回调中添加代码：if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.UPSIDE_DOWN_CAKE && ContextCompat.checkSelfPermission(...) == PERMISSION_GRANTED) { startPickMedia(); }
customers: ["广州欢牛"]
source: chat_history
tags: ["Android 14", "图片权限", "READ_MEDIA_VISUAL_USER_SELECTED", "部分照片", "IM-UIKit"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：IM UIKit Android 14图片权限适配

## 问题详情

**现象**：
Android 14授权部分照片后无法正常使用图片选择功能，已按文档适配仍有问题

**环境信息**：
- 平台：Android

## 排查过程

1. 检查权限适配 → 已按文档适配Android 14
2. 检查授权结果 → 部分照片授权后仍无法使用
3. 分析系统行为 → 系统层动作日志无法看出
4. 提供解决方案 → 在权限请求结果回调中添加特定代码

## 根因分析

Android 14部分照片授权后需要额外处理READ_MEDIA_VISUAL_USER_SELECTED权限

## 解决方案

在权限请求结果回调中添加代码：if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.UPSIDE_DOWN_CAKE && ContextCompat.checkSelfPermission(...) == PERMISSION_GRANTED) { startPickMedia(); }

## 其他触发场景

（无）
