---
track_type: 排查类
sub_type: 使用问题
product: 互动直播
feature: 播放器
platform: Android
title: NELivePlayer的pause方法只对点播生效对直播无效
root_cause: NELivePlayerController的pause方法设计仅支持点播场景（VOD），直播流不支持暂停操作
solution: 直播播放器pause无效：NELivePlayerController的pause/resume方法只对点播（VOD）生效，对直播流（LIVE）无效；如需暂停直播效果，需切换到点播模式或其他实现方式
customers: ["杭州小众圈科技-诗音&回音"]
source: chat_history
tags: ["NELivePlayer","pause","直播","点播"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：Android NELivePlayer的pause方法只对点播生效对直播无效

## 问题详情

**现象**：
客户调用pause方法暂停直播播放无效，播放器继续播放。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供pause调用代码截图 → 确认调用方式
2. 客服确认pause对直播无效 → 确认产品设计限制
3. 只对点播生效 → 确认技术原因

**关键发现**：NELivePlayerController的pause方法设计仅支持点播场景（VOD），直播流不支持暂停操作

## 问题原因

NELivePlayerController的pause方法设计仅支持点播场景（VOD），直播流不支持暂停操作

## 解决方案

直播播放器pause无效：NELivePlayerController的pause/resume方法只对点播（VOD）生效，对直播流（LIVE）无效；如需暂停直播效果，需切换到点播模式或其他实现方式

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
