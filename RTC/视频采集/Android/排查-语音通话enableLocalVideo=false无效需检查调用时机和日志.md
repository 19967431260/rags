---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 视频采集
platform: Android
title: 语音通话enableLocalVideo=false无效需检查调用时机和日志
root_cause: 应用层实际未正确调用enableLocalVideo(false)，日志显示只有一次true调用；需确保在语音通话中正确调用enableLocalVideo(false)且传入参数为false而非true
solution: 确保在语音通话开始后正确调用mRtcEx.enableLocalVideo(false)，参数必须为false（不是true）；可通过云信后台日志验证调用是否生效
customers: ["南宁市懂卿科技有限公司"]
source: chat_history
tags: ["enableLocalVideo","语音通话","Android","视频采集","RTC"]
created: 2025-08-22
updated: 2026-03-26
---

## 问题：Android 语音通话enableLocalVideo=false无效需检查调用时机和日志

## 问题详情

**现象**：
客户在单聊语音通话时调用enableLocalVideo(false)关闭画面，但审核监测仍能检测到画面。云信后台查询该时段只有一次enableLocalVideo调用记录（值为true）。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供channelId和UID请客服查询 → 获取查询信息
2. 客服查询日志发现在指定时间段内只有一次enableLocalVideo调用且参数为true → 日志确认
3. 客户确认在进入信令房间和进入RTC房间时都调用了 → 调用时机确认
4. 客服展示日志只有一次true调用 → 验证
5. 客服建议检查应用层调用情况 → 排查方向
6. 客户自行排查后确认解决了 → 验证

**关键发现**：应用层实际未正确调用enableLocalVideo(false)，日志显示只有一次true调用；需确保在语音通话中正确调用enableLocalVideo(false)且传入参数为false而非true

## 问题原因

应用层实际未正确调用enableLocalVideo(false)，日志显示只有一次true调用；需确保在语音通话中正确调用enableLocalVideo(false)且传入参数为false而非true。

## 解决方案

确保在语音通话开始后正确调用mRtcEx.enableLocalVideo(false)，参数必须为false（不是true）；可通过云信后台日志验证调用是否生效。

## 其他触发场景

（合并时在此处追加）
