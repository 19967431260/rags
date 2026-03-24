---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频设备管理
platform: Web
title: Safari浏览器无法获取扬声器列表
root_cause: 移动端浏览器限制，需要先请求一次设备才能获取列表，但移动端本身不支持获取扬声器列表
solution: 移动端无法获取扬声器列表，仅PC Web端支持该功能
customers: ['成都瑞安云科技股份有限公司']
source: chat_history
tags: ['getSpeakers', 'Safari', '扬声器', '移动端', 'NERTC']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Web Safari浏览器无法获取扬声器列表

## 问题详情

**现象**：
在苹果Safari浏览器中调用NERTC.getSpeakers()获取扬声器列表返回空数组，PC端可以正常获取

## 排查过程



## 问题原因

移动端浏览器限制，需要先请求一次设备才能获取列表，但移动端本身不支持获取扬声器列表

## 解决方案

移动端无法获取扬声器列表，仅PC Web端支持该功能

## 其他触发场景

（合并时在此处追加）
