---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 设备控制
platform: Uniapp
title: UniApp端muteLocalAudio实现闭麦/静音
root_cause: 误用enableLocalAudio（关闭自己麦克风）来尝试静音对方声音，应使用muteLocalAudio
solution: 使用this.engine.muteLocalAudio(true)关闭对方声音输出（静音）；muteLocalAudio只是设置音量，enableLocalAudio优先级更高。两者都要在进入房间后调用。
customers: ["云南深度科技有限公司"]
source: chat_history
tags: ["UniApp", "RTC", "muteLocalAudio", "静音", "enableLocalAudio"]
created: 2025-07-31
updated: 2026-03-26
---

## 问题：Uniapp UniApp端muteLocalAudio实现闭麦/静音

## 问题详情

**现象**：
客户想实现类似微信电话的静音功能，即点击后听不见对方说话。使用enableLocalAudio没效果。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：UniApp
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认需求：关闭声音输出（听对方说话静音） → 明确需求
2. 区分：enableLocalAudio是关闭自己麦克风采集，muteLocalAudio才是关闭对方声音输出 → 区分两个接口
3. 确认入参：muteLocalAudio(true)关闭对方声音输出 → 确认参数

**关键发现**：误用enableLocalAudio（关闭自己麦克风）来尝试静音对方声音，应使用muteLocalAudio

## 问题原因

误用enableLocalAudio（关闭自己麦克风）来尝试静音对方声音，应使用muteLocalAudio

## 解决方案

使用this.engine.muteLocalAudio(true)关闭对方声音输出（静音）；muteLocalAudio只是设置音量，enableLocalAudio优先级更高。两者都要在进入房间后调用。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
