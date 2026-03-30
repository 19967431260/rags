---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 实时音视频通话
platform: Android
title: RTC 2.0特定设备通话报错so加载失败
root_cause: X86架构设备上so文件加载失败
solution: 在gradle文件的abiFilters中去掉X86配置，X86设备可以使用arm的so文件。
customers: ["广州缙铖"]
source: chat_history
tags: ["RTC", "Android", "so加载", "X86", "abiFilters"]
created: 2025-05-07
updated: 2025-03-20
---

## 问题：Android RTC 2.0特定设备通话报错so加载失败

## 问题详情

**现象**：
云信2.0实时音视频通话时报错，特定型号设备(X86架构)必现问题，其他手机和非手机设备正常。

## 排查过程

**关键发现**：X86架构设备上so文件加载失败

## 问题原因

X86架构设备上so文件加载失败

## 解决方案

在gradle文件的abiFilters中去掉X86配置，X86设备可以使用arm的so文件。
