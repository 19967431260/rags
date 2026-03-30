---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频录制
platform: Web
title: Web端录制后半程坐席画面卡住问题
root_cause: 
solution: 详见正文。
customers: ["北京易诚互动"]
source: chat_history
tags: ["录制", "画面卡住", "Web", "上行视频", "enableLogUpload"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

录制文件后半程坐席端画面卡住，只有音频没有视频。录制全程7分07秒，1分50秒开始坐席画面卡住，虚拟背景还在，没有黑屏。

## 排查过程

1. 商务反馈录制后半程坐席画面卡住 → 要求提供录制SDK日志和坐席uid、卡住时间点
2. 确认通话双方互看互听是否正常 → 客户反馈是实时音通话本身有问题
3. 后台查看上行视频数据突然中断 → 无法确定具体原因（设备硬件异常/浏览器与系统异常/摄像头被占用）
4. 建议开启日志上报功能

## 根因分析

上行视频数据突然中断，具体原因需要详细日志排查

## 解决方案

在NERTC.createClient初始化前调用NERTC.Logger.enableLogUpload开启日志上报，下次复现后可查看详细日志排查
