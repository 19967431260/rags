---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成编译
platform: Android
title: Android Studio类导入失败编译器报红
root_cause: Android Studio编译器缓存或版本兼容性问题
solution: 升级Android Studio到最新版本可解决此类编译器问题
customers: ['江西闪招信息技术有限公司']
source: chat_history
tags: ['Android Studio', '编译器', '类导入', '报红', '缓存']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Android Android Studio类导入失败编译器报红

## 问题详情

**现象**：
集成IM UIKit后，Android Studio中类无法自动导入，手动导入也报红，但代码可以运行。

## 排查过程

1. 检查依赖是否正确引入
2. 尝试双击shift查找类
3. 检查IMKitClient.init参数
4. 尝试重新同步项目
5. 检查Android Studio版本

## 问题原因

Android Studio编译器缓存或版本兼容性问题

## 解决方案

升级Android Studio到最新版本可解决此类编译器问题

## 其他触发场景

（合并时在此处追加）
