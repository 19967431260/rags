---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 崩溃修复
platform: Windows
title: nstd::string rfind崩溃
root_cause: nstd::string实现问题，依赖上游代码
solution: 先转std::string处理，跟随60版本发布修复
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["崩溃", "nstd", "rfind", "Windows"]
created: 2025-11-04
updated: 2026-03-20
---

## 问题：Windows nstd::string rfind崩溃

## 问题详情

**现象**：
Windows端使用nstd::string的rfind方法时出现崩溃。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析崩溃堆栈 → 定位到rfind方法
2. 确认必现性
**关键发现**：nstd基础数据结构问题

**关键发现**：

## 问题原因

nstd::string实现问题，依赖上游代码

## 解决方案

先转std::string处理，跟随60版本发布修复

## 其他触发场景

