---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: uniapp分包
platform: Uniapp
title: uniapp小程序主包引入UIKit后体积超标
root_cause: uniapp小程序主包引入UIKit后体积过大超过小程序限制
solution: 建议将UIKit分包引入，或者按需引入UIKit组件而非全量引入。
customers: ["青岛唐柏世纪商贸有限公司"]
source: chat_history
tags: ["uniapp", "分包", "UIKit", "体积超标", "小程序"]
created: 2025-08-20
updated: 2026-03-26
---

## 问题：Uniapp uniapp小程序主包引入UIKit后体积超标

## 问题详情

**现象**：
uniapp小程序主包引入UIKit后体积超标。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：uniapp打包小程序
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：uniapp小程序主包引入UIKit后体积过大超过小程序限制

## 问题原因

uniapp小程序主包引入UIKit后体积过大超过小程序限制

## 解决方案

建议将UIKit分包引入，或者按需引入UIKit组件而非全量引入。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
