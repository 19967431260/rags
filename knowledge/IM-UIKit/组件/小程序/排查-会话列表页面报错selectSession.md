---
track_type: 排查类
sub_type: 组件问题
product: IM-UIKit
feature: 组件
platform: 小程序
title: 会话列表页面报错selectSession
root_cause: UIstore的方法名是selectedSession，调用时可能用的是selectSession。
solution: 检查调用方式，UIstore的方法名是selectedSession。如集成后报错，打印UIstore对象检查维护的对象是否正确。
customers: ['杭州泥鳅信息技术有限公司']
source: chat_history
tags: ['小程序', '会话列表', 'selectSession', '报错']
created: 2025-02-14
updated: 2026-03-23
---

## 问题：小程序 会话列表页面报错selectSession

## 问题详情

**现象**：
会话列表页面加载时报错TypeError: Cannot read property 'selectSession' of undefined，微信小程序中需要重新进入小程序才不报错。

**环境信息**：
- 平台：小程序
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

UIstore的方法名是selectedSession，调用时可能用的是selectSession。

## 解决方案

检查调用方式，UIstore的方法名是selectedSession。如集成后报错，打印UIstore对象检查维护的对象是否正确。

## 其他触发场景

（合并时在此处追加：`- [小程序] 会话列表页面报错selectSession，来源：['杭州泥鳅信息技术有限公司']，2026-03-23`）
