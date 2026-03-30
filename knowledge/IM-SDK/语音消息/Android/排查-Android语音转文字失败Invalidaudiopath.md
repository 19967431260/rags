---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Android
title: Android语音转文字失败Invalid audio path
root_cause: 本地路径没有该资源文件，不会自动下载网络文件
solution: SDK没有主动删除逻辑，可能是用户手动清除缓存导致
customers: ["北京久幺幺"]
source: chat_history
tags: ["语音转文字", "audio path", "Android", "本地文件"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Android语音转文字失败Invalid audio path

## 问题详情

**现象**：
语音消息转文字时报错Invalid audio path，本地路径没有资源文件

**环境信息**：
- 平台：Android

## 排查过程

1. 查看报错日志
2. 确认本地文件是否存在

## 根因分析

本地路径没有该资源文件，不会自动下载网络文件

## 解决方案

SDK没有主动删除逻辑，可能是用户手动清除缓存导致

## 其他触发场景

（无）
