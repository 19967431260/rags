---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 房间管理
platform: iOS
title: RTC加入房间返回30103 room not found
root_cause: 
solution: 初始化时设置loglevel=info，复现问题后提供NERTC日志进行分析
customers: ['VIP云信-邯郸市趣网传媒技术有限公司']
source: chat_history
tags: ['30103', 'room not found', '加入房间', 'RTC']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：iOS RTC加入房间返回30103 room not found

## 问题详情

**现象**：
音视频加入房间时偶尔返回错误：Error Domain=NERtcRemoteErrorDomain Code=30103 "room not found"，提示房间不存在

## 排查过程



## 问题原因



## 解决方案

初始化时设置loglevel=info，复现问题后提供NERTC日志进行分析

## 其他触发场景

（合并时在此处追加）
