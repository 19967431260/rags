---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: HarmonyOS
title: 鸿蒙推送报错action和uri不能同时为空
root_cause: clickAction中actionType为openCustomPage时，action和uri不能同时为空
solution: 参考华为推送文档配置clickAction参数，确保action或uri有值
customers: ["好未来-yach"]
source: chat_history
tags: ["鸿蒙", "推送", "clickAction", "action", "uri"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：鸿蒙推送报错action和uri不能同时为空

## 问题详情

**现象**：
鸿蒙推送返回错误：action and uri can't all be empty when actionType is openCustomPage。

**环境信息**：
- 平台：HarmonyOS

## 排查过程

1. 检查推送payload配置
2. 确认clickAction参数
3. 参考华为推送FAQ

## 根因分析

clickAction中actionType为openCustomPage时，action和uri不能同时为空

## 解决方案

参考华为推送文档配置clickAction参数，确保action或uri有值

## 其他触发场景

（无）
