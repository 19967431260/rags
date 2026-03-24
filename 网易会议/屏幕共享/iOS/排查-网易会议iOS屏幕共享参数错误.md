---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 屏幕共享
platform: iOS
title: 网易会议iOS屏幕共享参数错误
root_cause: 屏幕共享需要单独配置权限，与音视频权限不同。
solution: 屏幕共享有单独的权限配置，参考文档配置：https://doc.yunxin.163.com/meeting/guide/DU0NjE0MTI?platform=iOS
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['网易会议', 'Flutter', 'iOS', '屏幕共享', '权限']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：iOS 网易会议iOS屏幕共享参数错误

## 问题详情

**现象**：
客户反馈iOS屏幕共享配置后出现参数错误。

## 排查过程

1. 确认权限已处理 → 客户反馈权限已配置
2. 明确问题 → 屏幕共享有单独的权限配置
3. 提供文档 → 参考屏幕共享配置文档

## 问题原因

屏幕共享需要单独配置权限，与音视频权限不同。

## 解决方案

屏幕共享有单独的权限配置，参考文档配置：https://doc.yunxin.163.com/meeting/guide/DU0NjE0MTI?platform=iOS

## 其他触发场景

（合并时在此处追加）
