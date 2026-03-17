---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: Android端FCM离线推送收不到
root_cause: 设备网络无法访问FCM服务器导致推送token无法上报
solution: 排查设备网络环境,确保可以正常访问FCM服务器。建议更换网络环境测试
customers: ["深圳市哈雷彗星科技有限公司"]
source: chat_history
tags: ["FCM", "离线推送", "网络连接", "token上报", "Android"]
created: 2026-02-07
updated: 2026-03-17
---

## 问题：Android Android端FCM离线推送收不到

## 问题详情

**现象**：
FCM离线推送突然收不到,SDK日志显示FCM已注册,但在线时能收到消息,杀掉app后发送消息无法收到推送。设备VPN网络可以正常访问Google Play商店。

## 排查过程

1. 检查SDK日志 → 发现推送token没有上报
2. 重新登录拉取完整日志 → SDK日志中没有相关错误信息
3. 抓取logcat完整日志分析 → 发现网络无法访问FCM服务器,连接超时

**关键发现**：logcat日志显示设备网络无法访问FCM服务器,连接超时

## 问题原因

设备网络无法访问FCM服务器导致推送token无法上报

## 解决方案

排查设备网络环境,确保可以正常访问FCM服务器。建议更换网络环境测试

## 其他触发场景

