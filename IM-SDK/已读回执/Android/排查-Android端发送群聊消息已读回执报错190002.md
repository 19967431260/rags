---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 已读回执
platform: Android
title: Android端发送群聊消息已读回执报错190002
root_cause: SDK版本问题，最新版本已优化本地会话偶现问题
solution: 更新到最新SDK版本（优化了本地会话偶现问题），如更新后仍有问题需提供SDK日志进一步排查。
customers: ["上海猫头鹰投资有限公司"]
source: chat_history
tags: ["已读回执", "190002", "illegal state", "群聊", "Android"]
created: 2025-08-28
updated: 2026-03-26
---

## 问题：Android Android端发送群聊消息已读回执报错190002

## 问题详情

**现象**：
客户已开启已读回执功能（客户端和控制台均开启），发送群聊消息已读回执时报错：发送群聊消息已读回执失败, code: 190002, desc: illegal state。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
code: 190002, desc: illegal state

## 排查过程

1. 技术支持要求提供SDK日志排查 → 获取排查信息
2. 客户表示先更新最新SDK版本后再测试 → 确认为版本问题

**关键发现**：SDK版本问题，最新版本已优化本地会话偶现问题

## 问题原因

SDK版本问题，最新版本已优化本地会话偶现问题

## 解决方案

更新到最新SDK版本（优化了本地会话偶现问题），如更新后仍有问题需提供SDK日志进一步排查。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
