---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 房间管理
platform: Uniapp
title: uid超出JavaScript Number范围导致无法看到对方视频
root_cause: uid 值超出了 JavaScript Number 的安全整数范围（2^53-1），SDK 内部处理时 uid 被截断或错乱，导致远端视频无法正确渲染
solution: uid 必须控制在 JavaScript Number 安全范围内（建议不超过 9007199254740991）。如 uid 超出范围，需在业务层转换为字符串或缩短 uid 长度。
customers: ["成都神鸟互联网医院有限公司"]
source: chat_history
tags: ["uid","Number范围","视频看不见","JavaScript","MAX_SAFE_INTEGER"]
created: 2025-08-07
updated: 2026-03-26
---

## 问题：Uniapp uid超出JavaScript Number范围导致无法看到对方视频

## 问题详情

**现象**：
App 和 App 之间进行视频通话时，双方都看不见对方的视频（只能看见自己）。排查发现 uid 值为 8532624506323286041 等，超出了 JavaScript Number.MAX_SAFE_INTEGER（9007199254740991），导致 SDK 内部处理异常。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服排查 setupRemoteVideoCanvas 配置 → 配置排查
2. 客服发现 remoteUserIdVideoList 用数组循环处理 → 代码分析
3. 最终发现 uid 超出 JavaScript Number 安全范围 → 根因确认
4. 缩短短 uid 后问题解决 → 验证

**关键发现**：uid 值超出了 JavaScript Number 的安全整数范围（2^53-1），SDK 内部处理时 uid 被截断或错乱，导致远端视频无法正确渲染

## 问题原因

uid 值超出了 JavaScript Number 的安全整数范围（2^53-1），SDK 内部处理时 uid 被截断或错乱，导致远端视频无法正确渲染

## 解决方案

uid 必须控制在 JavaScript Number 安全范围内（建议不超过 9007199254740991）。如 uid 超出范围，需在业务层转换为字符串或缩短 uid 长度。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
