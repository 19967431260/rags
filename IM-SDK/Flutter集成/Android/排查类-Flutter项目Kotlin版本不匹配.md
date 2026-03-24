---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Flutter集成
platform: Android
title: Flutter项目Kotlin版本不匹配
root_cause: 项目环境设置问题，kotlin-gradle-plugin版本配置不正确
solution: 检查并统一build.gradle或build.gradle.kts中Kotlin插件版本，清理缓存后重新gradle。可在gradle.properties中强制指定kotlin.version=1.9.0
customers: ['宁波未科网络科技有限公司']
source: chat_history
tags: ['Flutter', 'Android', 'Kotlin', '版本不匹配', 'nim_core', 'gradle']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Flutter项目Kotlin版本不匹配

## 问题详情

**现象**：
Flutter项目运行Android时报错，提示Kotlin版本不匹配。iOS正常运行。

## 排查过程

1. 客户反馈flutter运行android报错
2. 确认使用nim_core: ^1.8.2
3. 建议升级Kotlin插件版本到1.9.0
4. 客户已使用1.9.0仍报错
5. 建议在gradle.properties中强制指定kotlin.version=1.9.0
6. 客户反馈1.7.1直接报错
7. 建议检查build.gradle中kotlin-gradle-plugin版本配置
8. 建议清理缓存重新gradle

## 问题原因

项目环境设置问题，kotlin-gradle-plugin版本配置不正确

## 解决方案

检查并统一build.gradle或build.gradle.kts中Kotlin插件版本，清理缓存后重新gradle。可在gradle.properties中强制指定kotlin.version=1.9.0

## 其他触发场景

（合并时在此处追加）
