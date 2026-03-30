---
track_type: 排查类
sub_type: 组件问题
product: IM-UIKit
feature: 会话列表
platform: Flutter
title: Flutter UIKit会话列表用户信息显示问题
root_cause: UIKit底层依赖的nim_core版本较老，超过阈值时不调用用户信息查询。
solution: 将IM SDK版本升级到1.8.3。querySessionList返回的结果没有user信息，user是在kit层通过其他逻辑组装的。如需手动查询，需拿到每个会话的accid再去查用户资料进行整合。
customers: ['杭州季多伊科技有限公司']
source: chat_history
tags: ['Flutter', 'UIKit', '会话列表', 'user为空', 'nim_core']
created: 2025-02-14
updated: 2026-03-23
---

## 问题：Flutter Flutter UIKit会话列表用户信息显示问题

## 问题详情

**现象**：
调用queryConversationList方法，当会话超过100条时返回的会话中user字段为空。

**环境信息**：
- 平台：Flutter
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

UIKit底层依赖的nim_core版本较老，超过阈值时不调用用户信息查询。

## 解决方案

将IM SDK版本升级到1.8.3。querySessionList返回的结果没有user信息，user是在kit层通过其他逻辑组装的。如需手动查询，需拿到每个会话的accid再去查用户资料进行整合。

## 其他触发场景

（合并时在此处追加：`- [Flutter] Flutter UIKit会话列表用户信息显示问题，来源：['杭州季多伊科技有限公司']，2026-03-23`）
