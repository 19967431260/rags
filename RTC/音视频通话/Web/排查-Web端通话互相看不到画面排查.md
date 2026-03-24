---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 音视频通话
platform: Web
title: Web端通话互相看不到画面排查
root_cause: 用户电脑摄像头设备状态异常，无法启动视频源
solution: 检查用户摄像头设备状态，必要时重启电脑恢复摄像头功能
customers: ['ISV云信-北京易诚互动-华侨银行']
source: chat_history
tags: ['WebRTC', '摄像头', '视频源', '通话异常']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Web Web端通话互相看不到画面排查

## 问题详情

**现象**：
客户反馈Web端和小程序端通话时互相看不到对方画面。排查发现Web端没有找到可用的摄像头资源。

## 排查过程

1. 确认问题现象：通话中互相看不到画面
2. 分析日志发现Web端报错：Could not start video source
3. 确认Web端没有找到可用的摄像头资源
4. 建议检查用户摄像头设备状态

## 问题原因

用户电脑摄像头设备状态异常，无法启动视频源

## 解决方案

检查用户摄像头设备状态，必要时重启电脑恢复摄像头功能

## 其他触发场景

（合并时在此处追加）
