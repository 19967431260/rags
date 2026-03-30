---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "初始化"
platform: "Android"
title: "小米机子release模式初始化失败"
root_cause: "小米系统对短时间内多次重启应用的机子会限制子进程启动，导致SDK初始化失败。另外useXLog高性能日志在release模式一般不需要开启。"
solution: "1. 避免短时间内多次重启应用
2. 初始化时将SDKOptions.useXLog设置为false，一般不需要高性能日志
3. release模式日志不打印在console，需要从日志文件中提取"
customers: ["FVIP云信-深圳富旅奇缘"]
source: "chat_history"
tags: ["初始化", "小米", "release", "useXLog", "子进程限制"]
created: "2025-09-10"
updated: "2026-03-20"
---

## 问题：Android 小米机子release模式初始化失败

## 问题详情

**现象**：
代码直接运行没问题，release模式初始化失败。

## 排查过程

1. 客户提供release模式日志
2. 分析日志发现是小米机子的限制
3. 确认短时间内重启应用多次，小米会限制子进程启动

## 问题原因

小米系统对短时间内多次重启应用的机子会限制子进程启动，导致SDK初始化失败。另外useXLog高性能日志在release模式一般不需要开启。

## 解决方案

1. 避免短时间内多次重启应用
2. 初始化时将SDKOptions.useXLog设置为false，一般不需要高性能日志
3. release模式日志不打印在console，需要从日志文件中提取

## 其他触发场景
