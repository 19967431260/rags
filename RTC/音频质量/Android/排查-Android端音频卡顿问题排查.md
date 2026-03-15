---
track_type: 排查类
sub_type: 性能问题
product: RTC
feature: 音频质量
platform: Android
title: Android端音频卡顿问题排查
root_cause: 音频采集频率不稳定导致卡顿
solution: 建议检查设备性能和后台进程占用情况，确保音频采集线程优先级足够高
customers: ['北京易连忆生']
source: chat_history
tags: ['音频卡顿', '采集不稳定', 'Android', '性能问题']
created: 2026-01-04
updated: 2026-03-15
---

## 问题：Android Android端音频卡顿问题排查

## 问题详情

用户反馈Android端音频卡顿，房间号：vmr_153414，用户ID：17572720，时间：2026-01-04 12:43

## 排查过程

1. 查看后台数据 → 音频发送正常
2. 检查网络质量 → 网络正常
3. 分析音频指标 → 发现音频采集不稳定

## 问题原因

音频采集频率不稳定导致卡顿

## 解决方案

建议检查设备性能和后台进程占用情况，确保音频采集线程优先级足够高
