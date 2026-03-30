---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 音视频通话
platform: Web
title: Web端必须使用HTTPS才能访问媒体设备
root_cause: 浏览器安全策略限制，HTTP协议无法访问摄像头和麦克风
solution: 必须使用HTTPS协议访问，这是浏览器的安全限制
customers: ["四川小凰科技有限公司"]
source: chat_history
tags: ["网易会议", "Web", "HTTPS", "媒体设备", "NOT_SUPPORT_ERROR"]
created: 2025-02-14
updated: 2026-03-23
---

## 问题：Web Web端必须使用HTTPS才能访问媒体设备

## 问题详情

**现象**：
Web端加入会议报错：浏览器不支持开启媒体设备，错误码NOT_SUPPORT_ERROR

**环境信息**：
- 平台：Web
- 产品：网易会议

**相关日志**：
错误码10001，提示浏览器不支持开启媒体设备

## 排查过程

1. 客户反馈Web端无法开启音视频
2. 查看日志发现错误码10001
3. 错误信息提示浏览器不支持开启媒体设备
4. 询问确认使用HTTP访问
5. 浏览器限制需要HTTPS才能使用媒体设备

**关键发现**：HTTP协议无法访问媒体设备

## 问题原因

浏览器安全策略限制，HTTP协议无法访问摄像头和麦克风

## 解决方案

必须使用HTTPS协议访问，这是浏览器的安全限制

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
