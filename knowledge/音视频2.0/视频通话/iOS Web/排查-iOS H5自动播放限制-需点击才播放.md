---
track_type: 排查类
sub_type: 使用问题
product: 音视频2.0
feature: 视频通话
platform: iOS Web
title: iOS H5远端视频需点击才播放：浏览器自动播放限制
root_cause: iOS浏览器自动播放策略限制，音频/视频无法自动播放，必须由用户手势触发
solution: 参考云信H5文档处理自动播放限制：需通过用户交互（如点击）触发音视频播放；可尝试通过Web Audio API绕过限制或引导用户进行交互操作；这是iOS Safari的固有限制。
customers: ["北京汉医健康科技"]
source: chat_history
tags: ["iOS", "H5", "自动播放", "点击播放", "Safari"]
created: 2025-07-02
updated: 2025-07-25
---

## 问题：iOS H5远端视频需点击才播放：浏览器自动播放限制

## 问题原因

iOS浏览器自动播放策略限制，音频/视频无法自动播放，必须由用户手势触发

## 解决方案

参考云信H5文档处理自动播放限制：需通过用户交互（如点击）触发音视频播放；可尝试通过Web Audio API绕过限制或引导用户进行交互操作；这是iOS Safari的固有限制。
