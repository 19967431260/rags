---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: 通用
title: @石志诚我现在遇到一个android问题，我
root_cause: ""
solution: "您现在调用的SDK日志发我们看下"
customers: ["ZVIP云信-广州史特岸科技有限公司"]
source: chat_history
tags: ["云信", "SDK", "技术支持"]
created: 2024-12-31
updated: 2026-03-20
---

## 问题：通用 @石志诚我现在遇到一个android问题，我

## 问题详情

**现象**：
@石志诚 我现在遇到一个android问题，我们使用你们的画布（NERtcVideoView），，我们现在全局使用的是一个单例的NERtcCallbackEx ，导致小窗口时候，释放这个activity里的NERtcVideoView无法释放掉，问一下这种怎么解决，
我们已经在ondestory的时候先调用了（ NERtcEx.getInstance().setupRemoteVideoCanvas(null, mNimId)
NERtcEx.getInstance().setupLocalVideoCanvas(null)） 这样不行

## 排查过程

1. 根据会话信息确认问题触发路径并复核关键配置。

## 问题原因

会话中未提供更细根因。

## 解决方案

您现在调用的SDK日志发我们看下
