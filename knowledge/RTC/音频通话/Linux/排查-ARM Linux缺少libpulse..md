---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音频通话
platform: Linux
title: ARM Linux缺少libpulse.so库导致RTC SDK无法运行
root_cause: ARM Linux系统缺少PulseAudio库，SDK强依赖该库
solution: 需要自行下载pulse audio源码编译安装到系统中，参考官网文档实现
customers: ['北京分音塔']
source: chat_history
tags: ['libpulse', 'ARM Linux', 'RTC', '音频', '依赖库']
created: 2025-09-22
updated: 2026-03-25
---

## 问题：Linux ARM Linux缺少libpulse.so库导致RTC SDK无法运行

## 问题详情

**现象**：
客户在ARM Linux设备(全志v851的arm a7处理器)上运行RTC SDK，提示缺少libpulse.so库，系统不支持pulse audio。

## 解决方案

需要自行下载pulse audio源码编译安装到系统中，参考官网文档实现
