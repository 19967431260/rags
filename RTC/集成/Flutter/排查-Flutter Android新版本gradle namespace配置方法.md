---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 集成
platform: Flutter
title: Flutter Android新版本gradle namespace配置方法
root_cause: 新版gradle要求明确声明namespace，而nertc_core模块未声明
solution: 在Android模块最外层build.gradle中添加：subprojects { if (project.name == "nertc_core") { project.afterEvaluate { android { namespace = "com.netease.nertcflutter" } } } }
customers: ["四创科技有限公司"]
source: chat_history
tags: ["Flutter","gradle","namespace","nertc_core","Android"]
created: 2025-08-26
updated: 2026-03-26
---

## 问题：Flutter Flutter Android新版本gradle namespace配置方法

## 问题详情

**现象**：
Flutter集成NERTC时Android端报gradle namespace相关错误，询问是否支持新版gradle的namespace。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Flutter + NERTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：新版gradle要求明确声明namespace，而nertc_core模块未声明

## 问题原因

新版gradle要求明确声明namespace，而nertc_core模块未声明。

## 解决方案

在Android模块最外层build.gradle中添加：subprojects { if (project.name == "nertc_core") { project.afterEvaluate { android { namespace = "com.netease.nertcflutter" } } } }

## 其他触发场景

（合并时在此处追加）
