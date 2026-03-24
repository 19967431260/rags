---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 屏幕共享
platform: Android
title: Android15屏幕共享帧率低/黑屏问题
root_cause: Android15屏幕共享时，如果用户选择错误应用(非当前应用)，系统回调给SDK的帧率极低或为空，导致共享画面黑屏或卡顿。
solution: 1. 升级SDK到5.x版本
2. 设置监听间隔：mRtcParameters.set(NERtcParameters.KEY_SCREEN_FREEZE_DURATION, 30)，在join前设置
3. 监听onWarning()错误码30022，当屏幕共享回调无帧时会触发
4. 也可设置旋转模式为byapp，5.x版本已兼容业务层旋转场景
customers: ['平安银行']
source: chat_history
tags: ['Android15', '屏幕共享', '黑屏', '帧率低', '30022', 'KEY_SCREEN_FREEZE_DURATION']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：Android Android15屏幕共享帧率低/黑屏问题

## 问题详情

**现象**：
客户在Android15上进行屏幕共享时，出现帧率极低(小于5帧)、码率低、画面黑屏的问题。

## 排查过程

1. 客户提供logcat日志 → 客服发现码率帧率都小于5帧，正常屏幕共享最少7-8帧
2. 客户对比正常场景 → 发现选择当前应用屏幕录制时正常
3. 研发分析 → 判断是Android15屏幕共享选错app导致回调帧率为空或极低
4. 提供临时方案 → 依赖local回调，选择错误应用时回调帧率稳定为2可作为判断依据
5. 最终方案 → SDK新增屏幕共享异常回调(错误码30022)

## 问题原因

Android15屏幕共享时，如果用户选择错误应用(非当前应用)，系统回调给SDK的帧率极低或为空，导致共享画面黑屏或卡顿。

## 解决方案

1. 升级SDK到5.x版本
2. 设置监听间隔：mRtcParameters.set(NERtcParameters.KEY_SCREEN_FREEZE_DURATION, 30)，在join前设置
3. 监听onWarning()错误码30022，当屏幕共享回调无帧时会触发
4. 也可设置旋转模式为byapp，5.x版本已兼容业务层旋转场景

## 其他触发场景

（合并时在此处追加）
