---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: Web
title: Web端显示多路流时画面叠加问题
root_cause: demo默认没有处理多路流的展示逻辑，需要根据uid和流类型设置不同的div
solution: 需要根据evt回调的uid和流类型，分别设置对应的画布。修改stream-added监听中的代码，根据uid和流类型设置不同的div
customers: ["西安优迈智慧矿山科技有限公司"]
source: chat_history
tags: ["音视频2.0","Web端","多路流显示","画布设置"]
created: 2025-05-23
updated: 2025-03-23
---

## 问题：Web Web端显示多路流时画面叠加问题

## 问题详情

**现象**：
Web端显示时，两个流在一个div里面叠加显示。

**环境信息**：
- 平台：Web
- 功能：RTC音视频通话

## 排查过程

1. 确认显示问题 → 两个流在一个div里面叠加显示
2. 分析demo逻辑 → demo默认没有处理多路流的展示逻辑
3. 确认解决方案 → 需要根据uid和流类型设置不同的div

**关键发现**：demo默认没有处理多路流的展示逻辑

## 问题原因

demo默认没有处理多路流的展示逻辑，需要根据uid和流类型设置不同的div。

## 解决方案

需要根据evt回调的uid和流类型，分别设置对应的画布。修改stream-added监听中的代码，根据uid和流类型设置不同的div。

## 其他触发场景

