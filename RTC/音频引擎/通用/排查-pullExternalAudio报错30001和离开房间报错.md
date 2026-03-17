---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频引擎
platform: 通用
title: pullExternalAudio报错30001和离开房间报错
root_cause: 加入房间时的30001错误：退房音频开启前设备还在打开，与调用时序有时差导致。离开房间错误：重复调用了leaveChannel接口
solution: 加入房间时的30001错误可以忽略，只要后续有数据就行，入会后才打开扬声器进行音频驱动。离开房间的错误是因为重复调用了leaveChannel，避免重复调用即可。
customers: ["北京分音塔"]
source: chat_history
tags: ["pullExternalAudio", "30001", "leaveChannel", "自定义音频", "重复调用"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：通用 pullExternalAudio报错30001和离开房间报错

## 问题详情

**现象**：
使用自定义音频输入时，加入房间后SDK日志打印30001错误，离开房间时也会打印错误，导致状态更新函数未被调用。SetExternalAudioRender设置采样率为16k，实际传给SDK的也是16k。

## 排查过程

1. 检查pullExternalAudio调用参数和采样率配置 → 确认都是16k，配置正确
2. 检查加入房间后的错误日志 → 发现有30001错误码
3. 检查离开房间的日志 → leaveChannel回调返回0成功，但有错误日志

**关键发现**：离开房间的错误是因为已经离开房间的情况下又调用了一次离开房间

## 问题原因

加入房间时的30001错误：退房音频开启前设备还在打开，与调用时序有时差导致。离开房间错误：重复调用了leaveChannel接口

## 解决方案

加入房间时的30001错误可以忽略，只要后续有数据就行，入会后才打开扬声器进行音频驱动。离开房间的错误是因为重复调用了leaveChannel，避免重复调用即可。

## 其他触发场景

（暂无）
