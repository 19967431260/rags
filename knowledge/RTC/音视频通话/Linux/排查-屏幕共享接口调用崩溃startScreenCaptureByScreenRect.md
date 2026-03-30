---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: Linux
title: 屏幕共享接口调用崩溃（startScreenCaptureByScreenRect）
root_cause: 使用默认参数导致崩溃
solution: 修改参数设置：NERtcScreenCaptureParameters para; para.enable_high_light = false; 然后调用rtc_engine->startScreenCaptureByScreenRect(NERtcRectangle(), NERtcRectangle(), para); 避免使用默认参数导致崩溃
customers: ["西安优迈智慧矿山科技有限公司"]
source: chat_history
tags: ["音视频2.0","屏幕共享","接口崩溃","Linux平台"]
created: 2025-05-23
updated: 2025-03-23
---

## 问题：Linux 屏幕共享接口调用崩溃（startScreenCaptureByScreenRect）

## 问题详情

**现象**：
客户调用屏幕共享接口时程序崩溃，返回30005错误。

**环境信息**：
- 平台：Linux
- 功能：RTC音视频通话

## 排查过程

1. 确认崩溃接口 → startScreenCaptureByScreenRect
2. 确认错误码 → 30005错误
3. 分析参数设置 → 使用默认参数导致崩溃
4. 确认解决方案 → 修改参数设置

**关键发现**：使用默认参数导致崩溃

## 问题原因

使用默认参数导致崩溃。

## 解决方案

修改参数设置：
```cpp
NERtcScreenCaptureParameters para;
para.enable_high_light = false;
rtc_engine->startScreenCaptureByScreenRect(NERtcRectangle(), NERtcRectangle(), para);
```

避免使用默认参数导致崩溃。

## 其他触发场景

