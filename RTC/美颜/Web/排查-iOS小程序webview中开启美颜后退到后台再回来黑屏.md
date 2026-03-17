---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 美颜
platform: Web
title: iOS小程序webview中开启美颜后退到后台再回来黑屏
root_cause: iOS在后台时系统会暂停渲染或终止内容进程或音视频会话。
solution: 监听页面回到前台事件，尝试使用resumeLiveStream重新渲染，如果恢复不了改成重新调用setDataSource重新拉流。H5环境不建议开启美颜。
customers: ["银河视界"]
source: chat_history
tags: ["黑屏","美颜","后台切换","iOS小程序"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Web iOS小程序webview中开启美颜后退到后台再回来黑屏

## 问题详情

**现象**：
iOS小程序中webview使用播放器播放低延时流，开启美颜后退到后台再回来出现黑屏状态。

## 问题原因

iOS在后台时系统会暂停渲染或终止内容进程或音视频会话。

## 解决方案

监听页面回到前台事件，尝试使用resumeLiveStream重新渲染，如果恢复不了改成重新调用setDataSource重新拉流。H5环境不建议开启美颜。

## 其他触发场景

