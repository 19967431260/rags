---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 白板文档展示
platform: 微信小程序
title: 小程序webview中PPT预览模糊问题
root_cause: PPT转码后的图片解析在小程序webview环境下存在兼容性问题
solution: 技术侧已定位问题并重启服务修复，建议客户重新上传PPT验证。
customers: ["智慧树"]
source: chat_history
tags: ["白板", "PPT模糊", "小程序", "webview", "文档转码"]
created: 2025-05-19
updated: 2025-03-20
---

## 问题：微信小程序 小程序webview中PPT预览模糊问题

## 问题详情

**现象**：
客户反馈在白板中转码后的PPT，在小程序webview中预览显示模糊，但web端清晰。

## 排查过程

**关键发现**：PPT转码后的图片解析在小程序webview环境下存在兼容性问题

## 问题原因

PPT转码后的图片解析在小程序webview环境下存在兼容性问题

## 解决方案

技术侧已定位问题并重启服务修复，建议客户重新上传PPT验证。
