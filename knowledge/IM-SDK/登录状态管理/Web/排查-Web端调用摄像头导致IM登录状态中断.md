---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录状态管理
platform: Web
title: Web端调用摄像头导致IM登录状态中断
root_cause: 系统浏览器限制，可能会把IM的长连接掐掉
solution: 调用IM接口判断登录状态，确保登录后再发送消息
customers: ['成都瑞安云科技股份有限公司']
source: chat_history
tags: ['illegal state', '登录状态', '摄像头', 'Web', '长连接']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：Web Web端调用摄像头导致IM登录状态中断

## 问题详情

**现象**：
在H5中调用手机摄像头拍照，打开摄像头后等待5-10秒再拍照发送，会被判定为IM未登录状态，立即拍照则能发送成功。报错：illegal state, Can not sendCmd due to no logined

## 排查过程



## 问题原因

系统浏览器限制，可能会把IM的长连接掐掉

## 解决方案

调用IM接口判断登录状态，确保登录后再发送消息

## 其他触发场景

（合并时在此处追加）
