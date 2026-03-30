---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频画面
platform: Android
title: Android端截图与视频画面镜像不一致
root_cause: NERtcVideoView默认前置摄像头开启镜像显示，而截图获取的是原始视频流，未经过镜像处理。
solution: 需要自行翻转截图后的画面以匹配视频预览效果。可以通过关闭NERtcVideoView的镜像显示，或在截图后对图片进行水平翻转处理。
customers: ['深圳初相位科技有限公司']
source: chat_history
tags: ['Android', '截图', '镜像', 'NERtcVideoView', '前置摄像头']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android Android端截图与视频画面镜像不一致

## 问题详情

**现象**：
Android端使用音视频2.0 SDK设置视频画面模式为全部填满显示，截图后在ImageView上显示时，画面镜像方向与视频预览不一致。例如视频画面中人靠左边，截图下来人在画面右边。

## 排查过程

1. 客户反馈截图后ImageView显示与视频预览不一致，存在镜像问题
2. 询问ImageView是否需要设置scaleType模式
3. 确认NERtcVideoView默认开启镜像显示，而截图获取的是原始视频流
4. 建议客户自行翻转截图后的画面

## 问题原因

NERtcVideoView默认前置摄像头开启镜像显示，而截图获取的是原始视频流，未经过镜像处理。

## 解决方案

需要自行翻转截图后的画面以匹配视频预览效果。可以通过关闭NERtcVideoView的镜像显示，或在截图后对图片进行水平翻转处理。

## 其他触发场景

（合并时在此处追加）
