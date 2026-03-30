---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 调试模式
platform: Electron
title: Electron SDK调试模式开启方法
root_cause: 
solution: 在控制台应用设置中开启调试模式，支持不传token或传正确token进行调试，不影响线上用户。
customers: ['西安美电智能科技有限公司']
source: chat_history
tags: ['Electron', '调试模式', 'token']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Electron Electron SDK调试模式开启方法

## 问题详情

**现象**：
客户集成Electron SDK时遇到token相关错误，需要开启调试模式。

**环境信息**：
- 平台：Electron
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认错误信息 → token相关错误
2. 建议开启调试模式 → 支持不传token或传正确token
3. 指导开启路径 → 控制台-应用-调试模式
4. 确认不影响线上 → 调试模式不影响线上用户

## 问题原因

（根因分析）

## 解决方案

在控制台应用设置中开启调试模式，支持不传token或传正确token进行调试，不影响线上用户。

## 其他触发场景

（合并时在此处追加：`- [Electron] Electron SDK调试模式开启方法，来源：['西安美电智能科技有限公司']，2026-03-23`）
