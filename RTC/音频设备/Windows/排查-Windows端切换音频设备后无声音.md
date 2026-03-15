---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频设备
platform: Windows
title: Windows端切换音频设备后无声音
root_cause: Windows端设备切换后SDK未正确处理音频流重定向
solution: 1.使用SDK提供的设备切换接口 2.确保在设备变更回调中正确处理 3.如问题持续，升级到最新SDK版本
customers: ['杭州晓宇-红蓝CP']
source: chat_history
tags: ['无声音', '音频设备', 'Windows', '设备切换']
created: 2026-01-20
updated: 2026-03-15
---

## 问题：Windows Windows端切换音频设备后无声音

## 问题详情

Windows端用户在通话过程中切换音频输出设备（如从扬声器切换到耳机），切换后无声音输出。需要重新进入房间才能恢复。

## 排查过程

1.用户反馈切换设备后无声音
2.检查设备切换接口调用
3.建议拉取日志分析

## 问题原因

Windows端设备切换后SDK未正确处理音频流重定向

## 解决方案

1.使用SDK提供的设备切换接口 2.确保在设备变更回调中正确处理 3.如问题持续，升级到最新SDK版本
