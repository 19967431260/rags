---
track_type: "排查类"
sub_type: "测试问题"
product: "RTC"
feature: "变声"
platform: "Web"
title: "SDK升级后变声失效且听不到声音"
root_cause: "remoStream.setAudioOutput()接口未传递设备ID参数，导致扬声器路由不正常"
solution: "调用remoStream.setAudioOutput()时传入正确的设备ID参数，确保扬声器路由正常。"
customers: ["河北宏筑建通"]
source: "chat_history"
tags: ["RTC", "Web", "变声", "setAudioOutput", "设备ID", "听不到声音"]
created: "2025-09-17"
updated: "2026-03-20"
---

## 问题：Web SDK升级后变声失效且听不到声音

## 问题详情

**现象**：
从5.6系列升级到5.8最新版本后，变声功能不稳定：1.进入会议是原声；2.后进会议的用户无法听到声音。

## 排查过程

1. 客户反馈升级后问题 → 技术支持分析\n2. 收集双方日志 → 发现接收方无输出设备\n3. 对比旧版本日志 → 确认设备检测问题\n4. 研发复现定位 → 发现remoStream.setAudioOutput()接口未传参\n**关键发现**：setAudioOutput接口未传设备ID导致扬声器路由异常

## 问题原因

remoStream.setAudioOutput()接口未传递设备ID参数，导致扬声器路由不正常

## 解决方案

调用remoStream.setAudioOutput()时传入正确的设备ID参数，确保扬声器路由正常。

## 其他触发场景
