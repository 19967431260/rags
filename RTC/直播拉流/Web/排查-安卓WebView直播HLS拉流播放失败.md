---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 直播拉流
platform: Web
title: 安卓WebView直播HLS拉流播放失败
root_cause: HTTPS页面加载HTTP视频流触发浏览器安全策略限制，以及企业微信内置WebView版本兼容性问题
solution: 使用HTTPS协议的HLS拉流地址，确保页面协议与视频流协议一致
customers: ["永安期货"]
source: chat_history
tags: ["直播", "HLS", "WebView", "MixedContent", "HTTPS"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：安卓WebView直播HLS拉流播放失败

## 问题详情

**现象**：
客户反馈安卓手机在企业微信内嵌浏览器和自有App内嵌WebView中播放直播HLS流时，出现播放失败报错(VIDEOJS ERROR CODE:4 MEDIA_ERR_SRC_NOT_SUPPORTED)，iOS正常，PC端正常。

**环境信息**：
- 平台：Web

## 排查过程

1. 确认拉流地址格式 → HLS格式正确
2. 检查网页协议 → 发现HTTPS页面加载HTTP视频流触发Mixed Content警告
3. 排查浏览器兼容性 → 企业微信内置WebView版本问题
4. 建议客户使用HTTPS拉流地址

## 根因分析

HTTPS页面加载HTTP视频流触发浏览器安全策略限制，以及企业微信内置WebView版本兼容性问题

## 解决方案

使用HTTPS协议的HLS拉流地址，确保页面协议与视频流协议一致

## 其他触发场景

（无）
