---
track_type: 咨询类
sub_type: 功能实现咨询
product: RTC
feature: 屏幕共享
platform: Electron
title: PC端音视频2.0 Electron demo咨询
root_cause: 音视频2.0 SDK要求VS2017及以上版本，与客户现有VS2013环境不兼容
solution: 提供音视频2.0 Electron demo和IM Electron demo
customers: ['广州群市网络科技有限公司']
source: chat_history
tags: ['RTC', '音视频2.0', 'Electron', 'VS2017', 'Windows']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：PC端音视频2.0 Electron demo咨询

## 问题详情

**现象**：
客户需要PC端音视频2.0 Electron demo，官网只有C++ demo，且客户项目使用VS2013开发，而音视频2.0要求VS2017+

## 排查过程

1. 客户反馈PC demo音视频无法使用，发现是音视频1.0 demo
2. 音视频1.0已停止维护，建议升级到2.0
3. 客户提供C++ demo，但开发环境是VS2013，而2.0要求VS2017+

## 问题原因

音视频2.0 SDK要求VS2017及以上版本，与客户现有VS2013环境不兼容

## 解决方案

提供音视频2.0 Electron demo和IM Electron demo

## 其他触发场景

（合并时在此处追加）
