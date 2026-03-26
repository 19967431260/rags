---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 依赖库
platform: iOS
title: iOS端SDWebImage报错Xcode版本过低
root_cause: SDWebImage库要求较高Xcode版本，低版本Xcode编译时报警告或报错
solution: 升级Xcode到最新稳定版本，或使用适配低版本Xcode的SDWebImage版本。
customers: ["成都超林科技有限公司"]
source: chat_history
tags: ["SDWebImage", "Xcode版本", "iOS", "依赖库"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：iOS iOS端SDWebImage报错Xcode版本过低

## 问题详情

**现象**：
iOS端SDWebImage报错Xcode版本过低。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：Xcode版本较低

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：SDWebImage库要求较高Xcode版本，低版本Xcode编译时报警告或报错

## 问题原因

SDWebImage库要求较高Xcode版本，低版本Xcode编译时报警告或报错

## 解决方案

升级Xcode到最新稳定版本，或使用适配低版本Xcode的SDWebImage版本。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
