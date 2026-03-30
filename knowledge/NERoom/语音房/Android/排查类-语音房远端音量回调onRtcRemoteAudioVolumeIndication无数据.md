---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 语音房
platform: Android
title: 语音房远端音量回调onRtcRemoteAudioVolumeIndication无数据
root_cause: 需进一步排查确认，可能与业务层逻辑或初始化顺序有关。
solution: 确保NEVoiceRoomKit.enableAudioVolumeIndication设置为true。如问题仍存在，需要提供复现路径、测试账号和验证app进一步排查。
customers: ['海南通通智能科技有限公司北京分公司']
source: chat_history
tags: ['语音房', 'onRtcRemoteAudioVolumeIndication', '音量回调', 'Android', 'enableAudioVolumeIndication']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：语音房远端音量回调onRtcRemoteAudioVolumeIndication无数据

## 问题详情

**现象**：
观众加入语音房上麦成功后有声音，但onRtcRemoteAudioVolumeIndication回调返回数据为空，totalVolume为0。主播端回调正常，只有观众端异常。

## 排查过程

1. 确认enableAudioVolumeIndication已设置；2. 本地onRtcLocalAudioVolumeIndication回调正常；3. 确认是远端回调无数据；4. 需要复现路径进一步排查。

## 问题原因

需进一步排查确认，可能与业务层逻辑或初始化顺序有关。

## 解决方案

确保NEVoiceRoomKit.enableAudioVolumeIndication设置为true。如问题仍存在，需要提供复现路径、测试账号和验证app进一步排查。

## 其他触发场景

（合并时在此处追加）
