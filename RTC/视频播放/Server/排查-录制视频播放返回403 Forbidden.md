---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频播放
platform: Server
title: 录制视频播放返回403 Forbidden
root_cause: URL鉴权开启导致直接访问视频链接被拒绝。
solution: 在控制台关闭URL鉴权，或携带wsSecret和wsTime参数访问。
customers: ['深圳市玩转魔方科技有限公司']
source: chat_history
tags: ['403', '视频播放', 'URL鉴权']
created: 2025-02-26
updated: 2026-03-23
---

## 问题：Server 录制视频播放返回403 Forbidden

## 问题详情

**现象**：
直接播放录制的视频返回403 Forbidden错误。

**环境信息**：
- 平台：Server
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认视频URL可访问性 → 403错误
2. 检查URL鉴权配置 → 发现鉴权开启
3. 关闭URL鉴权 → 问题解决

## 问题原因

URL鉴权开启导致直接访问视频链接被拒绝。

## 解决方案

在控制台关闭URL鉴权，或携带wsSecret和wsTime参数访问。

## 其他触发场景

（合并时在此处追加：`- [Server] 录制视频播放返回403 Forbidden，来源：['深圳市玩转魔方科技有限公司']，2026-03-23`）
