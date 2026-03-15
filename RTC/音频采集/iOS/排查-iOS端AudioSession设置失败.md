---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音频采集
platform: iOS
title: iOS端AudioSession设置失败导致无声音
root_cause: AudioSession被更高优先级的音频占用，导致SDK无法获取音频权限；同时客户端网络存在问题，视频stun探测包超时。
solution: 1. 排查是否有其他应用占用AudioSession，确保通话时音频权限可用。2. 检查网络环境，确保UDP端口连通性，特别是4200-4209端口段。3. 可监听ICE异常回调（基于5.x版本提供），及时感知媒体连接异常。
customers: ["平安银行"]
source: chat_history
tags: ["iOS", "AudioSession", "音频", "无声音", "网络", "stun"]
created: 2026-01-06
updated: 2026-03-15
---

## 问题：iOS iOS端AudioSession设置失败导致无声音

## 问题详情

**现象**：
iOS端通话过程中坐席听不到客户声音，日志显示AudioSession设置失败，并且重试也无效。现象：前面几笔通话看不到也听不到，最后一笔看到画面但听不到声音。

## 排查过程

1. 检查日志 → 发现AudioSession设置失败且重试无效
2. 查看服务端录制文件 → 客户的视频和音频文件有生成但无数据
3. 检查媒体连接状态 → 加入房间后不久媒体连接就断开
**关键发现**：AudioSession被占用，每5秒重试一次均失败；视频stun包发送超时。

## 问题原因

AudioSession被更高优先级的音频占用，导致SDK无法获取音频权限；同时客户端网络存在问题，视频stun探测包超时。

## 解决方案

1. 排查是否有其他应用占用AudioSession，确保通话时音频权限可用。2. 检查网络环境，确保UDP端口连通性，特别是4200-4209端口段。3. 可监听ICE异常回调（基于5.x版本提供），及时感知媒体连接异常。

## 其他触发场景

（合并时在此处追加）
