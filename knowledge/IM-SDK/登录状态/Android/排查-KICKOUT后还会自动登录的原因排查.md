---
track_type: 排查类
sub_type: 业务逻辑问题
product: IM-SDK
feature: 登录状态
platform: Android
title: KICKOUT后还会自动登录的原因排查
root_cause: KICKOUT后业务层代码自动调用了login接口，导致看起来像'自动登录'。KICKOUT本身不会触发自动登录。
solution: KICKOUT后需要用户重新触发登录操作，业务层不要在收到KICKOUT回调时自动调用login。
customers: ["树兰医院-dx"]
source: chat_history
tags: ["KICKOUT","自动登录","manual login","登录状态","observeOnlineStatus"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：Android KICKOUT后还会自动登录的原因排查

## 问题详情

**现象**：
用户收到KICKOUT回调后，过一会竟然自动登录成功了感觉很奇怪。日志显示KICKOUT后立即有manual login调用。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

拉取SDK日志确认：KICKOUT后立即有do user manual login，说明是业务层主动调用了login接口 → 根因确认

**关键发现**：KICKOUT后业务层代码自动调用了login接口，导致看起来像'自动登录'。KICKOUT本身不会触发自动登录。

## 问题原因

KICKOUT后业务层代码自动调用了login接口，导致看起来像'自动登录'。KICKOUT本身不会触发自动登录。

## 解决方案

KICKOUT后需要用户重新触发登录操作，业务层不要在收到KICKOUT回调时自动调用login。

## 其他触发场景

（合并时在此处追加）
