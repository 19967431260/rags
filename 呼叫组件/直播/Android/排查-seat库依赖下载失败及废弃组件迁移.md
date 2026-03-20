---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 直播
platform: Android
title: seat库依赖下载失败及废弃组件迁移
root_cause: seat库已废弃停止维护
solution: 1. 提供seat库源码本地下载维护；2. 建议迁移到基于NERtc房间的互动直播方案：https://doc.yunxin.163.com/interactive-streaming/guide/jI1ODI2ODY?platform=android
customers: ["杭州裕隆通信有限公司"]
source: chat_history
tags: ["seat", "直播", "组件废弃", "互动直播"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Android seat库依赖下载失败及废弃组件迁移

## 问题详情

**现象**：
客户项目中的com.netease.yunxin.kit:seat:0.0.0-SNAPSHOT依赖无法下载，该库已停止维护。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈seat库无法下载
2. 确认该库已废弃不再维护
3. 提供源码本地下载方案
4. 建议迁移到互动直播方案

**关键发现**：

## 问题原因

seat库已废弃停止维护

## 解决方案

1. 提供seat库源码本地下载维护；2. 建议迁移到基于NERtc房间的互动直播方案：https://doc.yunxin.163.com/interactive-streaming/guide/jI1ODI2ODY?platform=android

## 其他触发场景

