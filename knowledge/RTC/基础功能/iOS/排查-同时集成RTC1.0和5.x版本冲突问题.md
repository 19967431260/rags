---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 基础功能
platform: iOS
title: iOS同时集成RTC1.0和5.x版本冲突问题
root_cause: 项目同时集成了RTC 1.0和5.x版本，导致NMCBasic等库冲突
solution: "1. RTC 5.x版本没有用到NMCBasic，可以删除1.0版本\n2. 确认NIMSDK版本兼容性\n3. 清理重复集成的库\n4. 重新编译验证"
customers:
  - 上海越约
source: chat_history
tags:
  - SDK
created: "2025-06-02"
updated: "2025-06-02"
---

## 问题：iOS同时集成RTC 1.0和5.x版本冲突问题

## 问题详情

**现象**：
项目同时集成了RTC 1.0和5.x版本，出现库冲突问题。

**环境信息**：
- 平台：iOS
- 集成方式：CocoaPods + 本地集成
- 涉及库：NMCBasic等

## 排查过程

1. **版本确认** → 检查集成版本
   - 项目同时存在RTC 1.0和5.x版本
   - 另一个项目没有1.0版本就没有问题

2. **库依赖分析** → 确认NMCBasic使用情况
   - RTC 5.x版本没有用到NMCBasic
   - 可以删除1.0版本的库

3. **SDK版本检查** → 确认NIMSDK版本
   - 查看包里面的info文件确认版本号

**关键发现**：RTC 5.x不依赖NMCBasic，可以删除1.0版本解决冲突

## 问题原因

1. **版本冲突**：同时集成两个版本的RTC SDK
2. **库重复**：1.0版本的库在5.x中已不再使用
3. **编译冲突**：重复库导致编译或运行时错误

## 解决方案

1. **删除1.0版本**：
   - 移除RTC 1.0版本的库
   - 清理NMCBasic等不再使用的库

2. **版本确认**：
   - 检查NIMSDK版本兼容性
   - 查看info文件确认版本号

3. **重新编译**：
   - 清理构建缓存
   - 重新编译验证

## 其他触发场景

