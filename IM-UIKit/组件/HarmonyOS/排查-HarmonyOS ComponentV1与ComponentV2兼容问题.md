---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 组件
platform: HarmonyOS
title: HarmonyOS ComponentV1与ComponentV2兼容问题
root_cause: ComponentV1和ComponentV2不兼容
solution: 建议升级到ComponentV2，毕竟ComponentV2是新的，后面大概是需要升级的
customers: ["VIP_云信-杭州泰阿网络"]
source: chat_history
tags: ["HarmonyOS","ComponentV1","ComponentV2","UIKit"]
created: 2025-08-28
updated: 2026-03-26
---

## 问题：HarmonyOS HarmonyOS ComponentV1与ComponentV2兼容问题

## 问题详情

**现象**：
客户反馈外面使用的ComponentV1，云信里面用的V2，导致报错 Cannot assign the ComponentV1 value to the ComponentV2 for the property 'pathStack'

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认是鸿蒙UIKit组件使用了ComponentV2，项目本身使用的是ComponentV1 → 确认根因

**关键发现**：ComponentV1和ComponentV2不兼容

## 问题原因

ComponentV1和ComponentV2不兼容

## 解决方案

建议升级到ComponentV2，毕竟ComponentV2是新的，后面大概是需要升级的

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
