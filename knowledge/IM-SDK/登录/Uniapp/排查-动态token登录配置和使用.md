---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: Uniapp
title: 动态token登录配置和使用
root_cause: 需要在控制台勾选动态token配置，并在代码中正确配置tokenProvider。
solution: 1. 控制台开启动态token功能
2. 配置tokenProvider提供返回token的函数，token可从后端获取或按规则生成
3. 动态token设置为1即开启
customers: ['VIP云信-深圳市找大状']
source: chat_history
tags: ['动态token', '登录', 'Uniapp', 'tokenProvider', '控制台']
created: 2025-02-18
updated: 2026-03-23
---

## 问题：Uniapp 动态token登录配置和使用

## 问题详情

**现象**：
Uniapp使用动态token登录时控制台报错，不清楚动态token如何传入。

**环境信息**：
- 平台：Uniapp
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认控制台已开启动态token开关
2. 检查tokenProvider配置

## 问题原因

需要在控制台勾选动态token配置，并在代码中正确配置tokenProvider。

## 解决方案

1. 控制台开启动态token功能
2. 配置tokenProvider提供返回token的函数，token可从后端获取或按规则生成
3. 动态token设置为1即开启

## 其他触发场景

（合并时在此处追加：`- [Uniapp] 动态token登录配置和使用，来源：['VIP云信-深圳市找大状']，2026-03-23`）
