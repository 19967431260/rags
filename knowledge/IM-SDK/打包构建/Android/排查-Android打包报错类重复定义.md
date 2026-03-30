---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 打包构建
platform: Android
title: Android打包报错类重复定义
root_cause: chatkit-ui库重复依赖导致类冲突
solution: 检查依赖树，排除重复的chatkit-ui依赖，确保只有一个版本被引入
customers: ["江西闪招信息技术有限公司"]
source: chat_history
tags: ["Android", "打包", "依赖冲突", "chatkit-ui", "重复定义"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android打包报错类重复定义

## 问题详情

**现象**：
客户反馈Android项目打包时报错，提示com.netease.yunxin.kit.chatkit.ui.ActivityWorkaround类重复定义。

**环境信息**：
- 平台：Android

## 排查过程

1. 检查依赖冲突 → 使用./gradlew :app:dependencies --configuration releaseRuntimeClasspath查看依赖树
2. 查找重复库 → 检查com.netease.yunxin.kit:chatkit-ui是否重复依赖
3. 建议clean工程 → 多次clean后仍有问题

## 根因分析

chatkit-ui库重复依赖导致类冲突

## 解决方案

检查依赖树，排除重复的chatkit-ui依赖，确保只有一个版本被引入

## 其他触发场景

（无）
