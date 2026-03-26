---
track_type: 排查类
sub_type: 配置类
product: IM-SDK
feature: 会话管理
platform: 通用
title: 会话置顶功能报错110306 conversation stick top disabled
root_cause: 应用未开通会话置顶功能，SDK侧校验失败返回110306
solution: 在云信控制台开启会话置顶功能：全局功能 → 会话置顶 → 开启
customers: ["树兰医院-dx"]
source: chat_history
tags: ["会话置顶","110306","控制台","V2NIM","conversation stick top"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：通用 会话置顶功能报错110306 conversation stick top disabled

## 问题详情

**现象**：
调用V10会话置顶接口时报错：code: 110306, message: 'conversation stick top disabled'。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

客服确认是功能未在控制台开通导致 → 根因确认

**关键发现**：应用未开通会话置顶功能，SDK侧校验失败返回110306

## 问题原因

应用未开通会话置顶功能，SDK侧校验失败返回110306。

## 解决方案

在云信控制台开启会话置顶功能：全局功能 → 会话置顶 → 开启。

## 其他触发场景

（合并时在此处追加）
