---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频通话
platform: 通用
title: 视频通话接通后无画面但语音正常-UI遮挡问题
root_cause: RTC画布被其他UI遮挡，导致视频画面不可见
solution: 在onFirstVideoFrameRender回调中加判定，当渲染帧来了之后判断当前UI状态，避免遮挡RTC画布
customers: ["VIP云信-河南趋前网络科技有限公司"]
source: chat_history
tags: ["视频通话", "黑屏", "UI遮挡", "onFirstVideoFrameRender", "相芯美颜"]
created: 2026-02-09
updated: 2026-03-15
---

## 问题：通用 视频通话接通后无画面但语音正常-UI遮挡问题

## 问题详情

**现象**：
用户视频接通后无视频画面，但语音正常。接听方看呼叫方没有画面，部分通话截图显示有画面，部分确实没有画面。通话ID：6041723，主叫9735，被叫322617。

## 排查过程

1. 检查服务端数据 → 上下行码率正常，有渲染帧率
2. 确认本地预览 → 呼叫方9735本地预览也是黑屏
3. 排查美颜 → 使用相芯美颜
4. 分析录屏 → 有语音无画面，疑似UI遮挡
**关键发现**：服务端数据显示有画布并渲染，语音正常说明连通性正常，大概率是RTC画布被其他UI遮挡

## 问题原因

RTC画布被其他UI遮挡，导致视频画面不可见

## 解决方案

在onFirstVideoFrameRender回调中加判定，当渲染帧来了之后判断当前UI状态，避免遮挡RTC画布
