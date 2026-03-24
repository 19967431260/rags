---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: Web
title: Web端摄像头调用失败NotReadableError
root_cause: 浏览器返回NotReadableError，无法获取摄像头视频流，可能因摄像头被占用、系统权限或浏览器问题
solution: 捕获NotReadableError报错，提示用户检查摄像头是否被占用或重启浏览器/设备
customers: ['广东医群科技有限公司']
source: chat_history
tags: ['NotReadableError', '摄像头', 'WebRTC', '音视频', 'getUserMedia']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Web Web端摄像头调用失败NotReadableError

## 问题详情

**现象**：
Web端音视频通话SDK偶尔出现摄像头调用失败，localStream.init()初始化出错，报错NotReadableError。挂断重新接通后恢复正常。

## 排查过程

1. 客户提供日志
2. 技术支持分析日志发现错误：[NERTC:ERROR:3274] getStream error: NotReadableError Could not start video source
3. 确认摄像头资源被占用或浏览器无法获取视频流

## 问题原因

浏览器返回NotReadableError，无法获取摄像头视频流，可能因摄像头被占用、系统权限或浏览器问题

## 解决方案

捕获NotReadableError报错，提示用户检查摄像头是否被占用或重启浏览器/设备

## 其他触发场景

（合并时在此处追加）
