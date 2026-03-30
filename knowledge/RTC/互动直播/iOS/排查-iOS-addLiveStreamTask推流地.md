---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 互动直播
platform: iOS
title: addLiveStreamTask推流地址与应用不匹配导致拉流失败
root_cause: addLiveStreamTask设置的推拉流地址需要是本应用下的，客户使用了原应用的拉流地址，而RTC功能开通在新应用上。
solution: 确保addLiveStreamTask设置的streamURL和拉流地址都是当前应用(2ac91c4dd9d8160ed0ba96fb1a44b970)下的，不同应用的推拉流地址不能混用。
customers: ["FVIP云信-上海功途教育"]
source: chat_history
tags: ["addLiveStreamTask", "拉流失败", "AppKey", "推流地址"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：iOS addLiveStreamTask推流地址与应用不匹配导致拉流失败

## 问题详情

**现象**：
addLiveStreamTask返回成功，但拉流地址无法观看。客户更换了AppKey后出现问题。

## 排查过程

1. 检查推流返回 → addLiveStreamTask返回0表示成功
2. 检查拉流地址 → 发现拉流地址是原应用(edf0438994bc1e44d6ca85b8fb2537b2)的，而RTC功能开通在新应用(2ac91c4dd9d8160ed0ba96fb1a44b970)上
**关键发现**：推流地址和RTC功能不在同一应用下

## 问题原因

addLiveStreamTask设置的推拉流地址需要是本应用下的，客户使用了原应用的拉流地址，而RTC功能开通在新应用上。

## 解决方案

确保addLiveStreamTask设置的streamURL和拉流地址都是当前应用(2ac91c4dd9d8160ed0ba96fb1a44b970)下的，不同应用的推拉流地址不能混用。

## 其他触发场景

