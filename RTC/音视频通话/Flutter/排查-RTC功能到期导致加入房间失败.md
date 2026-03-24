---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: Flutter
title: RTC功能到期导致加入房间失败
root_cause: RTC功能到期未续费，导致无法使用音视频通话功能。
solution: 联系商务重新开通RTC功能。403错误表示没有权限使用RTC功能。
customers: ['FRIENDLINK LIMITED']
source: chat_history
tags: ['RTC', 'Flutter', '403', '功能到期']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Flutter RTC功能到期导致加入房间失败

## 问题详情

**现象**：
Flutter接入Android视频通话无法成功，joinChannel返回403错误。

## 排查过程

1. 客户反馈Flutter无法成功接入视频通话
2. 查看日志发现joinChannel返回403
3. 检查appkey发现RTC功能已到期
4. 建议联系商务重新开通
5. 客户后续反馈token校验错误（414）

## 问题原因

RTC功能到期未续费，导致无法使用音视频通话功能。

## 解决方案

联系商务重新开通RTC功能。403错误表示没有权限使用RTC功能。

## 其他触发场景

（合并时在此处追加）
