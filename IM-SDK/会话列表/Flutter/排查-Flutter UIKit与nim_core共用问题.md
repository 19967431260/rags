---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 会话列表
platform: Flutter
title: Flutter UIKit与nim_core共用问题
root_cause: UIKit和nim_core共用实例，重复登录导致逻辑问题。
solution: UIKit封装了nim_core调用逻辑，直接使用UIKit的登录即可，无需单独登录nim_core。
customers: ['深圳问津']
source: chat_history
tags: ['Flutter', 'UIKit', 'nim_core', '登录']
created: 2025-02-25
updated: 2026-03-23
---

## 问题：Flutter Flutter UIKit与nim_core共用问题

## 问题详情

**现象**：
Flutter端使用UIKit会话列表为空，咨询是否可以与nim_core一起使用。

**环境信息**：
- 平台：Flutter
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认登录方式 → 先登录nim_core再登录UIKit
2. 分析问题 → 重复登录导致逻辑冲突
3. 确认解决方案 → 只使用UIKit的登录

## 问题原因

UIKit和nim_core共用实例，重复登录导致逻辑问题。

## 解决方案

UIKit封装了nim_core调用逻辑，直接使用UIKit的登录即可，无需单独登录nim_core。

## 其他触发场景

（合并时在此处追加：`- [Flutter] Flutter UIKit与nim_core共用问题，来源：['深圳问津']，2026-03-23`）
