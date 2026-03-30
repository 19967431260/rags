---
track_type: 咨询类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: Uniapp
title: Uniapp音视频通话呼叫邀请实现方案
root_cause: 纯音视频SDK在加入房间前不创建长连接，无法直接实现呼叫功能
solution: 1. 使用uni-im发送自定义消息实现呼叫邀请
2. 纯音视频SDK配合uni-im的长连接能力
3. 通过uni-push推送到被叫用户
4. 被叫用户收到邀请后加入房间
customers: ['重庆简房科技']
source: chat_history
tags: ['Uniapp', '音视频通话', '呼叫邀请', 'uni-im', '自定义消息']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：Uniapp音视频通话呼叫邀请实现方案

## 问题详情

**现象**：
已接入uni-im，想在基础上增加音视频通话功能，但纯音视频没有账号体系无法做呼叫功能。

## 排查过程

1. 确认纯音视频SDK没有长连接，无法直接做呼叫
2. 确认uni-im已有长连接能力
3. 分析呼叫邀请的实现方案

## 问题原因

纯音视频SDK在加入房间前不创建长连接，无法直接实现呼叫功能

## 解决方案

1. 使用uni-im发送自定义消息实现呼叫邀请
2. 纯音视频SDK配合uni-im的长连接能力
3. 通过uni-push推送到被叫用户
4. 被叫用户收到邀请后加入房间

## 其他触发场景

（合并时在此处追加）
