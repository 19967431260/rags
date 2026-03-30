---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 会议加入
platform: 通用
title: 加入会议使用meetingNum而非meetingId
root_cause: ""
solution: /v2/info/接口要用会议号meetingNum，不能用meetingId
customers: ["和仁"]
source: chat_history
tags: ["加入会议","meetingNum","meetingId","会议号"]
created: 2026-02-01
updated: 2026-03-17
---

## 问题：通用 加入会议使用meetingNum而非meetingId

## 问题详情

**现象**：
预约了会议，会议在时间范围内，meetingId也生成了，但加入会议时显示未找到该会议。

## 排查过程

排查过程未在会话中详细记录。

**关键发现**：使用了meetingId而非meetingNum

## 问题原因

根因未明确记录

## 解决方案

/v2/info/接口要用会议号meetingNum，不能用meetingId。

## 其他触发场景

（暂无）
