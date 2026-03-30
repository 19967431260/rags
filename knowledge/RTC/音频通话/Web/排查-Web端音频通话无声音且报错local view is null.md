---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频通话
platform: Web
title: Web端音频通话无声音且报错local view is null
root_cause: 缺少音频流的DOM容器元素
solution: 给一个不实际渲染的div作为音频流容器即可解决。
customers: ["湖南有人网络科技有限公司"]
source: chat_history
tags: ["RTC", "Web", "音频通话", "local view is null", "DOM容器"]
created: 2026-02-10
updated: 2026-03-17
---

## 问题：Web Web端音频通话无声音且报错local view is null

## 问题详情

**现象**：
客户在Web端测试语音通话时，调用浏览器麦克风成功但没有声音，输入和输出都没反应。控制台报错：RTCController playLocalStream failed: {"message":"local view is null"}

## 问题原因

缺少音频流的DOM容器元素

## 解决方案

给一个不实际渲染的div作为音频流容器即可解决。

## 其他触发场景
