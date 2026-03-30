---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 网络连接
platform: Web
title: Web端音视频通话双方看不见视频
root_cause: https://nrtc.netease.im/nrtc/getChannelInfos.action 和 weblink.netease.im 域名网络不通，可能是代理配置问题
solution: 需要检查对以下域名的代理配置是否正确：
1. https://nrtc.netease.im/nrtc/getChannelInfos.action
2. weblink.netease.im

确保这些域名在防火墙/代理中正确放行。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# Web端音视频通话双方看不见视频

## 问题描述

客户反馈年前正常，年后所有用户都出现音视频通话双方看不见视频的问题

## 问题背景

- 检查日志中的网络请求和域名连接情况

## 根因分析

https://nrtc.netease.im/nrtc/getChannelInfos.action 和 weblink.netease.im 域名网络不通，可能是代理配置问题

## 解决方案

需要检查对以下域名的代理配置是否正确：
1. https://nrtc.netease.im/nrtc/getChannelInfos.action
2. weblink.netease.im

确保这些域名在防火墙/代理中正确放行。

## 标签

- RTC
- Web
- 视频不通
- 域名
- 代理
- 网络配置

## 客户

- ISV云信-北京易诚互动-华侨银行

## 会话日期

2025-02-08
