---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: 微信小程序
title: 小程序推流成功但App端看不到视频问题
root_cause: 小程序端publish调用不正确或live-pusher组件配置问题
solution: 1. 确认正确调用client.publish进行发布；2. 检查mediaType设置；3. 检查live-pusher组件配置，确保debug、autopush、enable-mic、enable-camera等参数正确
customers: ["潍坊眼科医院有限责任公司"]
source: chat_history
tags: ["小程序","推流","App","视频","排查"]
created: 2025-05-09
updated: 2025-03-23
---

## 问题：微信小程序 小程序推流成功但App端看不到视频问题

## 问题详情

**现象**：
小程序端开启视频后，手机端能监听到有人加入房间，但看不到视频和声音，小程序上能看到自己的视频。

**环境信息**：
- 平台：微信小程序
- 功能：RTC音视频通话

## 排查过程

1. 确认小程序端发布状态 → 检查是否正确调用了client.publish进行发布
2. 检查mediaType设置 → 确认mediaType参数设置是否正确
3. 开启debug模式 → 初始化时将debug设为true，重新初始化复现进房到开视频过程
4. 检查live-pusher组件配置 → 确保debug、autopush、enable-mic、enable-camera等参数正确设置
5. 参考微信小程序官方文档 → 检查组件状态和配置

**关键发现**：问题通常由publish调用不正确或live-pusher组件配置不当导致

## 问题原因

小程序端推流配置不正确，可能是以下原因之一：
1. 未正确调用client.publish进行发布
2. mediaType设置不正确
3. live-pusher组件配置参数有误

## 解决方案

1. **确认publish调用**：确保小程序端正确调用了client.publish进行发布
2. **检查mediaType**：确认mediaType设置正确
3. **开启debug模式**：初始化时将debug设为true，重新初始化复现进房到开视频过程，查看日志
4. **检查组件配置**：检查live-pusher组件配置，确保以下参数正确设置：
   - debug
   - autopush
   - enable-mic
   - enable-camera
5. **参考官方文档**：参考微信小程序官方文档检查组件状态

## 其他触发场景

