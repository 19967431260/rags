---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 设备控制
platform: Uniapp
title: UniApp端setSpeakerphoneOn入参传错导致切换失败
root_cause: setSpeakerphoneOn入参传错，应该是true切换到扬声器，false切换到听筒；同时带耳机时接口不生效
solution: setSpeakerphoneOn(true)切换到扬声器，setSpeakerphoneOn(false)切换到听筒。注意：带耳机或连接蓝牙耳机时此接口不生效。
customers: ["云南深度科技有限公司"]
source: chat_history
tags: ["UniApp", "RTC", "setSpeakerphoneOn", "扬声器", "听筒"]
created: 2025-07-31
updated: 2026-03-26
---

## 问题：Uniapp UniApp端setSpeakerphoneOn入参传错导致切换失败

## 问题详情

**现象**：
客户在UniApp中使用RTC SDK，调用setSpeakerphoneOn切换扬声器时参数传错：enableLocalAudio传入false导致setSpeakerphoneOn也传了false，实际应该传true才能切换到扬声器。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：UniApp
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈切换没效果 → 确认现象
2. 检查日志发现入参为false → 定位入参错误
3. 确认：true才是切换到扬声器，false是听筒 → 明确参数含义
4. 带耳机或蓝牙耳机时此接口不生效 → 补充限制条件

**关键发现**：setSpeakerphoneOn入参传错，应该是true切换到扬声器，false切换到听筒

## 问题原因

setSpeakerphoneOn入参传错，应该是true切换到扬声器，false切换到听筒；同时带耳机时接口不生效

## 解决方案

setSpeakerphoneOn(true)切换到扬声器，setSpeakerphoneOn(false)切换到听筒。注意：带耳机或连接蓝牙耳机时此接口不生效。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
