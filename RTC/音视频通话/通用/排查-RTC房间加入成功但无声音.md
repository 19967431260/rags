---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: 通用
title: RTC房间加入成功但无声音
root_cause: 1. RTC加入房间时uid参数使用了字符串"net_ease_1"而非数字类型，导致鉴权失败用户未能真正加入房间；2. 另一用户调用了enableLocalAudio(false)主动关闭了本地音频采集。
solution: 1. RTC的uid参数必须使用数字类型（如1、2、100等），不能使用字符串；\n2. 确认未在业务逻辑中调用enableLocalAudio(false)，如需开启音频调用enableLocalAudio(true)；\n3. 如果需要静音进入房间后再开启，应调用muteLocalAudio(mute: true)而非enableLocalAudio(false)。
customers: ["佰亿汇（西安）网络科技有限公司"]
source: chat_history
tags: ["RTC","uid","enableLocalAudio","无声音","字符串"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：通用 RTC房间加入成功但无声音

## 问题详情

**现象**：
用户进入RTC房间后通话无声音，另一用户也反馈听不到。日志显示加入房间成功，但实际只有一个用户真正加入了房间。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认加入房间日志 → 显示成功
2. 拉取服务端日志 → 发现只有1个用户真正在房间内
3. 排查另一个用户 → UID设置为字符串"net_ease_1"而非数字
4. 确认SDK要求 → RTC的uid参数必须是数字类型
5. 进一步确认 → 另一用户调用了enableLocalAudio(false)禁用了本地音频

**关键发现**：RTC加入房间时uid参数使用了字符串"net_ease_1"而非数字类型，导致鉴权失败用户未能真正加入房间；另一用户调用了enableLocalAudio(false)主动关闭了本地音频采集。

## 问题原因

RTC加入房间时uid参数使用了字符串"net_ease_1"而非数字类型，导致鉴权失败用户未能真正加入房间；另一用户调用了enableLocalAudio(false)主动关闭了本地音频采集。

## 解决方案

1. RTC的uid参数必须使用数字类型（如1、2、100等），不能使用字符串；
2. 确认未在业务逻辑中调用enableLocalAudio(false)，如需开启音频调用enableLocalAudio(true)；
3. 如果需要静音进入房间后再开启，应调用muteLocalAudio(mute: true)而非enableLocalAudio(false)。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
