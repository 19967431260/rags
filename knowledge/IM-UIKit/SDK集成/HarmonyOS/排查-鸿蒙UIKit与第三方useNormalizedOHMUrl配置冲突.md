---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: SDK集成
platform: HarmonyOS
title: 鸿蒙UIKit与第三方useNormalizedOHMUrl配置冲突
root_cause: 使用的UIKit组件版本过老，与最新版存在配置差异
solution: 升级UIKit组件到最新版本即可解决useNormalizedOHMUrl配置冲突问题
customers: ["上海抱朴"]
source: chat_history
tags: ["HarmonyOS", "UIKit", "useNormalizedOHMUrl", "ohpm", "版本升级", "第三方冲突"]
created: 2025-07-04
updated: 2025-07-25
---

## 问题：HarmonyOS UIKit与第三方useNormalizedOHMUrl配置冲突

## 问题详情

**现象**：
客户集成云信带UI的SDK（UIKit），与第三方库冲突。第三方要求useNormalizedOHMUrl=true，但SDK配置要求不一致，ohpm报本地依赖名不匹配错误。

**复现步骤**：
1. 使用带UI的SDK集成到HarmonyOS项目
2. 第三方要求useNormalizedOHMUrl=true
3. ohpm报本地依赖名不匹配错误

## 排查过程

1. 客户提供报错日志（ohpm依赖名不匹配错误）
2. 核查报错：`@nimkit/coreKit`等包名与oh-package.json5中声明不匹配
3. 确认为UIKit组件版本过老
4. 建议升级到最新版本

**关键发现**：UIKit组件版本过老导致与第三方配置冲突，升级到最新版本可解决。

## 问题原因

使用的UIKit组件版本过老，与最新版存在配置差异，ohpm包名解析与第三方库冲突。

## 解决方案

升级UIKit组件到最新版本即可解决useNormalizedOHMUrl配置冲突问题。
