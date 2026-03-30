---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: Android
title: SDK降级导致被踢登录问题
root_cause: SDK新版本在device id后增加时间戳检查，覆盖降级后首次会判定为新设备
solution: 等待云信提供针对回退场景优化的新版本SDK
customers: ['新视展']
source: chat_history
tags: ['kickout', 'device id', 'SDK降级', '9.16.700', '9.16.500']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Android SDK降级导致被踢登录问题

## 问题详情

**现象**：
Android端IM SDK从9.16.700降级回9.16.500后会被踢出登录，返回kickout错误码。原因是新版本在device id后增加时间戳检查，覆盖降级后首次会判定为新设备。

## 排查过程

1. 客户反馈升级9.16.700再降级回9.16.500会被踢出登录
2. 技术支持确认覆盖安装后device id变化导致服务器判定为新设备
3. 研发确认新版本为适配一键迁移问题增加了时间戳检查
4. 针对回退场景优化，提供新版本解决

## 问题原因

SDK新版本在device id后增加时间戳检查，覆盖降级后首次会判定为新设备

## 解决方案

等待云信提供针对回退场景优化的新版本SDK

## 其他触发场景

（合并时在此处追加）
