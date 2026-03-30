---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 播放器SDK
platform: Linux
title: 国产化播放器SDK崩溃及拉流异常
root_cause: sdl库不匹配导致崩溃，节点测速逻辑在linux下有问题
solution: 更新到LivePlayer-SDK-1.7.1版本，优化了节点测速逻辑并修复偶发崩溃。Linux依赖ffmpeg(3.4.13)和sdl2(2.32)。
customers: ["成都东方闻道"]
source: chat_history
tags: ["播放器", "崩溃", "Linux", "国产化", "sdl"]
created: 2025-05-12
updated: 2025-03-20
---

## 问题：Linux 国产化播放器SDK崩溃及拉流异常

## 问题详情

**现象**：
Linux国产化环境下播放器SDK出现崩溃和拉流异常问题，涉及统信UOS系统。

## 排查过程

**关键发现**：sdl库不匹配导致崩溃，节点测速逻辑在linux下有问题

## 问题原因

sdl库不匹配导致崩溃，节点测速逻辑在linux下有问题

## 解决方案

更新到LivePlayer-SDK-1.7.1版本，优化了节点测速逻辑并修复偶发崩溃。Linux依赖ffmpeg(3.4.13)和sdl2(2.32)。
