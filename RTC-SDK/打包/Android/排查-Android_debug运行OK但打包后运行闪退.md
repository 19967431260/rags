---
track_type: 排查类
sub_type: 集成类
product: RTC-SDK
feature: 打包
platform: Android
title: Android debug运行OK但打包后运行闪退
root_cause: Android打包后运行闪退可能是SDK依赖冲突或混淆配置问题
solution: 检查SDK依赖冲突，添加必要的keep规则到proguard配置中。
customers: ["河南瓜虫网络科技有限公司"]
source: chat_history
tags: ["Android", "打包", "闪退", "debug", "混淆"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：Android Android debug运行OK但打包后运行闪退

## 问题详情

**现象**：
Android debug运行正常但打包后运行闪退。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：Android打包后运行闪退可能是SDK依赖冲突或混淆配置问题

## 问题原因

Android打包后运行闪退可能是SDK依赖冲突或混淆配置问题

## 解决方案

检查SDK依赖冲突，添加必要的keep规则到proguard配置中。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
