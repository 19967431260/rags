---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音频设备
platform: Android
title: Android端通话关闭扬声器后音频仍从扬声器输出
root_cause: RTC SDK初始化后默认使用扬声器，在加入房间前未正确关闭扬声器，导致后续切换受影响。客户的v消息主叫一开始就调用setMode3，影响了setSpeakerphoneOn的效果。
solution: 正确的调用时机：在SDK init成功之后、join房间之前，调用setLoudspeakerMode(false)关闭扬声器，然后再加入房间。这是推荐的标准接入方案。
customers: ["vivo-v消息"]
source: chat_history
tags: ["setLoudspeakerMode","扬声器","听筒","Android","RTC"]
created: 2025-08-04
updated: 2026-03-26
---

## 问题：Android Android端通话关闭扬声器后音频仍从扬声器输出

## 问题详情

**现象**：
在通话过程中调用关闭扬声器接口（setLoudspeakerMode），API返回成功但音频实际仍从扬声器输出，不是预期的听筒。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认客户操作 → 在通话中调用关闭扬声器
2. 确认问题表现 → 回调显示切换成功但实际通道不对
3. 确认SDK默认行为 → 默认使用扬声器播放
4. 与研发确认正确方案 → init之后、join房间之前关闭扬声器再加入

**关键发现**：RTC SDK初始化后默认使用扬声器，在加入房间前未正确关闭扬声器，导致后续切换受影响。客户的v消息主叫一开始就调用setMode3，影响了setSpeakerphoneOn的效果。

## 问题原因

RTC SDK初始化后默认使用扬声器，在加入房间前未正确关闭扬声器，导致后续切换受影响。客户的v消息主叫一开始就调用setMode3，影响了setSpeakerphoneOn的效果。

## 解决方案

正确的调用时机：在SDK init成功之后、join房间之前，调用setLoudspeakerMode(false)关闭扬声器，然后再加入房间。这是推荐的标准接入方案。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
