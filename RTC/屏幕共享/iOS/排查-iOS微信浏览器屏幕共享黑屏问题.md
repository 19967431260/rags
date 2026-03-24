---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 屏幕共享
platform: iOS
title: iOS微信浏览器屏幕共享黑屏问题
root_cause: iOS微信内置浏览器对屏幕共享的兼容性限制，非SDK问题
solution: 建议用户使用Safari浏览器或其他支持的浏览器进入会议室观看屏幕共享
customers: ['江苏华招网信息技术有限公司']
source: chat_history
tags: ['屏幕共享', '黑屏', 'iOS', '微信浏览器', '兼容性']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：iOS iOS微信浏览器屏幕共享黑屏问题

## 问题详情

**现象**：
iOS设备从微信内嵌浏览器进入会议室，观看屏幕共享时显示黑屏，但在Safari浏览器中正常显示。

## 排查过程

1. 确认问题仅在微信浏览器中出现，Safari/钉钉/其他浏览器正常
2. 检查屏幕共享测试demo是否正常
3. 确认iOS微信浏览器对WebRTC屏幕共享的支持限制

## 问题原因

iOS微信内置浏览器对屏幕共享的兼容性限制，非SDK问题

## 解决方案

建议用户使用Safari浏览器或其他支持的浏览器进入会议室观看屏幕共享

## 其他触发场景

（合并时在此处追加）
