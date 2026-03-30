---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: ICE连接
platform: Android
title: 视频通话无法建立ICE连接
root_cause: 可能是VPN或网络环境问题导致ICE连接失败
solution: 检查是否开启VPN，如未开启可尝试切换到4G网络测试
customers: ["深圳市镜玩-觅伊"]
source: chat_history
tags: ["RTC","ICE","连接失败","VPN","网络"]
created: 2025-02-24
updated: 2025-03-20
---

## 问题：Android 视频通话无法建立ICE连接

## 问题详情

**现象**：
视频通话无法建立成功，信令连接成功但媒体ICE连接失败。

## 排查过程

1. 分析日志发现ICE连接一直失败 → 确认ICE问题
2. 怀疑网络环境问题 → 定位可能原因

**关键发现**：可能是VPN或网络环境问题

## 问题原因

可能是VPN或网络环境问题导致ICE连接失败。

## 解决方案

检查是否开启VPN，如未开启可尝试切换到4G网络测试。

## 其他触发场景

