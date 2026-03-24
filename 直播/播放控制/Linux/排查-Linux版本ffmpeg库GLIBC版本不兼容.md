---
track_type: 排查类
sub_type: 集成类
product: 直播
feature: 播放控制
platform: Linux
title: Linux版本ffmpeg库GLIBC版本不兼容
root_cause: ffmpeg在ubuntu 20.04上编译，依赖较高版本GLIBC
solution: 客户根据环境自行编译ffmpeg，需要开启--enable-decoder=h264 --enable-decoder=aac --enable-protocol=rtmp等选项
customers: ["成都东方闻道科技"]
source: chat_history
tags: ["播放器", "Linux", "ffmpeg", "GLIBC"]
created: 2025-02-26
updated: 2025-03-20
---

## 问题：Linux Linux版本ffmpeg库GLIBC版本不兼容

## 问题详情

**现象**：
播放器SDK Linux版本中的ffmpeg库依赖GLIBC_2.29，但客户机子版本是GLIBC 2.28。

**环境信息**：
- 平台：Linux
- GLIBC版本：2.28（客户环境）vs 2.29（SDK依赖）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取关键排查步骤，无则省略）

**关键发现**：（从会话提取关键发现，无则省略）

## 问题原因

ffmpeg在ubuntu 20.04上编译，依赖较高版本GLIBC。

## 解决方案

客户根据环境自行编译ffmpeg，需要开启--enable-decoder=h264 --enable-decoder=aac --enable-protocol=rtmp等选项。

## 其他触发场景
