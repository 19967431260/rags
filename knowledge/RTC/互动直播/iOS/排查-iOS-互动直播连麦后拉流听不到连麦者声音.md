---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 互动直播
platform: iOS
title: 互动直播连麦后拉流听不到连麦者声音
root_cause: 推流任务的layout.users中只配置了主播自己的信息，未添加连麦者的uid，导致连麦者的声音和视频未被推流出去。
solution: 连麦者上麦后，主播端需要在updateLiveStreamTask的layout.users中添加连麦者的uid配置，包含音频和视频推送设置。
customers: ["FVIP云信-上海功途教育"]
source: chat_history
tags: ["互动直播", "连麦", "拉流", "updateLiveStreamTask", "users"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：iOS 互动直播连麦后拉流听不到连麦者声音

## 问题详情

**现象**：
主播与连麦者可以互相语音通话，但观看端拉流只能听到主播声音，听不到连麦者声音。

## 排查过程

1. 检查推流任务 → 发现更新推流任务失败
2. 分析原因 → 连麦者在观看端调用addLiveStreamTask报错30003，因为已存在相同taskId的推流任务
3. 指导正确流程 → 主播端应在收到对端开启麦克风回调后调用updateLiveStreamTask更新推流布局
**关键发现**：需要在推流任务的layout.users中添加连麦者的uid配置

## 问题原因

推流任务的layout.users中只配置了主播自己的信息，未添加连麦者的uid，导致连麦者的声音和视频未被推流出去。

## 解决方案

连麦者上麦后，主播端需要在updateLiveStreamTask的layout.users中添加连麦者的uid配置，包含音频和视频推送设置。

## 其他触发场景

