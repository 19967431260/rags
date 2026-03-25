---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: Linux
title: pushExternalVideoFrame接口调用崩溃问题
root_cause: RTC engine未初始化完成就push数据、数据格式不正确、两个应用使用同一个uid
solution: 1. 确保摄像头数据回调回来时，RTC engine已经初始化完成；2. 在onJoinChannel回调成功后再push；3. 使用bool值做判断标志；4. 确保数据格式正确（如NV12格式）；5. 检查是否两个应用使用了同一个uid加入音视频房间
customers: ["西安优迈智慧矿山科技有限公司"]
source: chat_history
tags: ["音视频2.0","外部视频采集","程序崩溃","Linux平台"]
created: 2025-05-23
updated: 2025-03-23
---

## 问题：Linux pushExternalVideoFrame接口调用崩溃问题

## 问题详情

**现象**：
客户调用pushExternalVideoFrame接口时程序崩溃，报段错误。

**环境信息**：
- 平台：Linux
- 功能：RTC音视频通话

## 排查过程

1. 确认崩溃时机 → 调用pushExternalVideoFrame接口时
2. 检查engine状态 → 是否已初始化完成
3. 检查数据格式 → 是否正确组装数据
4. 检查uid冲突 → 是否有多个应用使用同一个uid

**关键发现**：多种原因可能导致接口调用崩溃

## 问题原因

1. RTC engine未初始化完成就push数据
2. 数据格式不正确
3. 两个应用使用同一个uid加入音视频房间

## 解决方案

1. **确保engine初始化完成**：确保摄像头数据回调回来时，RTC engine已经初始化完成
2. **正确时机push**：在onJoinChannel回调成功后再push
3. **使用标志位**：使用bool值做判断标志
4. **确保数据格式正确**：确保数据格式正确（如NV12格式）
5. **检查uid冲突**：检查是否两个应用使用了同一个uid加入音视频房间

## 其他触发场景

