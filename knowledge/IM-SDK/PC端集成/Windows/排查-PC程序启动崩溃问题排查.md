---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: PC端集成
platform: Windows
title: PC程序启动崩溃问题排查
root_cause: 崩溃发生在客户应用层代码，非SDK层问题。
solution: 研发分析dmp文件后反馈崩溃在应用层，建议客户自行检查应用层代码。
customers: ["eight roi sparta"]
source: chat_history
tags: ["PC崩溃", "Windows", "dmp文件", "应用层崩溃", "启动崩溃"]
created: 2025-06-22
updated: 2025-03-23
---

## 问题：Windows PC程序启动崩溃问题排查

## 问题详情

**现象**：
用户反馈PC端程序点开就崩溃，仅单个用户出现此问题，其他用户正常。客户提供崩溃截图和dmp文件。

## 排查过程

1. 获取崩溃信息 → 客户提供dmp格式崩溃文件
2. 确认IM版本 → 基于官网demo简单修改页面
3. 分析崩溃堆栈 → 研发分析dmp文件
4. 关键发现 → 崩溃发生在应用层（密信.exe）

**关键发现**：崩溃发生在客户应用层代码，非SDK层问题

## 问题原因

崩溃发生在客户应用层代码，非SDK层问题。

## 解决方案

研发分析dmp文件后反馈崩溃在应用层，建议客户自行检查应用层代码。

## 其他触发场景

