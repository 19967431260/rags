---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送channel_id未生效导致只收到3条
root_cause: OPPO推送需要正确配置channel_id，且需要使用支持channel_id的SDK版本
solution: 确保使用支持channel_id的OPPO推送SDK，并在配置中正确设置channel_id。
customers: ["武汉市渺寇午科技有限公司"]
source: chat_history
tags: ["OPPO推送", "channel_id", "3条", "Android"]
created: 2025-08-18
updated: 2026-03-26
---

## 问题：Android OPPO推送channel_id未生效导致只收到3条

## 问题详情

**现象**：
OPPO推送channel_id未生效导致只收到3条消息。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：OPPO设备

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

**关键发现**：OPPO推送需要正确配置channel_id，且需要使用支持channel_id的SDK版本

## 问题原因

OPPO推送channel_id未生效导致只收到3条消息

## 解决方案

确保使用支持channel_id的OPPO推送SDK，并在配置中正确设置channel_id。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
