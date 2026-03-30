---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 房间管理
platform: Flutter
title: 加入会议失败RTC功能未开通
root_cause: RTC功能未开通或试用期结束
solution: 在控制台开通RTC功能（音视频通话功能），开通后即可正常创建RTC房间并加入会议
customers: ['深圳市森愈网络科技有限公司']
source: chat_history
tags: ['RTC', '加入会议失败', 'netcall.g2', '功能开通']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Flutter 加入会议失败RTC功能未开通

## 问题详情

**现象**：
客户加入会议失败，日志显示createRtcRoom fail because netcall.g2 is closed

## 排查过程

1. 客户反馈加入会议失败 → 检查日志发现createRtcRoom失败
2. 日志显示netcall.g2 is closed → 判断RTC功能未开通或已到期
3. 客户开通RTC功能后问题解决

## 问题原因

RTC功能未开通或试用期结束

## 解决方案

在控制台开通RTC功能（音视频通话功能），开通后即可正常创建RTC房间并加入会议

## 其他触发场景

（合并时在此处追加）
