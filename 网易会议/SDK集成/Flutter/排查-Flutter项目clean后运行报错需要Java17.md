---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: SDK集成
platform: Flutter
title: Flutter项目clean后运行报错需要Java17
root_cause: 网易会议Flutter SDK需要Java17环境，客户项目配置的是低版本JDK
solution: 在Android Studio设置中将Gradle JDK设置为jbr 17，然后重新clean和pub get
customers: ["海南温蒂科技有限公司"]
source: chat_history
tags: ["Flutter", "Java17", "网易会议", "clean", "pub get"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Flutter项目clean后运行报错需要Java17

## 问题详情

**现象**：
客户Flutter项目在执行clean和pub get后运行报错，提示需要Java17环境。

**环境信息**：
- 平台：Flutter

## 排查过程

1. 检查当前Java版本 → 低于17
2. 修改Android Studio设置 → 将Gradle JDK设置为jbr 17
3. 重新clean和pub get → 问题解决

## 根因分析

网易会议Flutter SDK需要Java17环境，客户项目配置的是低版本JDK

## 解决方案

在Android Studio设置中将Gradle JDK设置为jbr 17，然后重新clean和pub get

## 其他触发场景

（无）
