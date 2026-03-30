---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频录制
platform: Server
title: 录制文件下载链接eventType=3无录制文件
root_cause: 
solution: 详见正文。
customers: ["宇为"]
source: chat_history
tags: ["录制", "eventType=3", "抄送", "服务端"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

收到eventType=3的录制文件下载抄送消息，但管理后台查不到录制文件ID，也没有实际下载到文件。

## 排查过程

客户咨询eventType=3录制文件下载抄送 → 查询记录发现该房间没有录制文件
→ 确认只有这一通没有录制
→ 判断该通通话没有开启录制任务

## 根因分析

该通通话未开启录制任务

## 解决方案

eventType=3消息不代表一定有录制文件，需确认通话是否开启了录制任务
