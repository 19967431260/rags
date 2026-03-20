---
track_type: 排查类
sub_type: 客户开发能力
product: RTC
feature: 屏幕共享
platform: HarmonyOS
title: 鸿蒙端无法显示对方辅流画面
root_cause: 画布设置时机不对，在onUserJoin时设置导致黑屏
solution: 一定要在NERtcVideoView的onLoad回调里设置画布和订阅，不能放在onUserJoin里
customers: ["深圳康佳"]
source: chat_history
tags: ["RTC", "鸿蒙", "辅流", "屏幕共享", "黑屏", "setupRemoteSubStreamVideoCanvas", "onLoad"]
created: 2025-11-27
updated: 2026-03-20
---

## 问题：HarmonyOS 鸿蒙端无法显示对方辅流画面

## 问题详情

**现象**：
NERTC_Harmony_SDK_v5.8.20，加入房间后能传输本地声音到对方Android，但显示不了对方辅流画面。已调用setupRemoteSubStreamVideoCanvas和subscribeRemoteSubStreamVideo，result返回0，也有onUserSubStreamVideoStart。

## 排查过程

1. 确认房间信息和UID
2. 收集鸿蒙和Android日志
3. 对比Demo测试
4. 分析画布设置
**关键发现**：Demo能看到画面，问题在画布设置时机，需要在NERtcVideoView的onLoad回调里设置画布和订阅

## 问题原因

画布设置时机不对，在onUserJoin时设置导致黑屏

## 解决方案

一定要在NERtcVideoView的onLoad回调里设置画布和订阅，不能放在onUserJoin里

## 其他触发场景

