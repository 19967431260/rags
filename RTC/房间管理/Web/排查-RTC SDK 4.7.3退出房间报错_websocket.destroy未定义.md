---
track_type: "排查类"
sub_type: "使用问题"
product: "RTC"
feature: "房间管理"
platform: "Web"
title: "RTC SDK 4.7.3退出房间报错_websocket.destroy未定义"
root_cause: "SDK 4.7.3版本存在bug"
solution: "研发会发hotfix版本修复，等待升级"
customers: ["北京汉医健康科技"]
source: "chat_history"
tags: ["RTC", "Web", "4.7.3", "leave", "websocket"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：Web RTC SDK 4.7.3退出房间报错_websocket.destroy未定义

## 问题详情

**现象**：
Web SDK升级到4.7.3后，调用Client.leave()后虽然执行.then()回调，但SDK底层报错'this._websocket.destroy' is undefined，再次加入房间也会报错。

## 排查过程

客户提供日志后，技术支持确认问题

## 问题原因

SDK 4.7.3版本存在bug

## 解决方案

研发会发hotfix版本修复，等待升级

## 其他触发场景
