---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 屏幕共享
platform: Rooms
title: Rooms设备看不到特定用户的屏幕共享
root_cause: Rooms版本未更新到最新版本，且下行网络条件差导致拉到最低分辨率的流
solution: 升级Rooms到最新2.2.2版本，检查网络条件
customers: ["四川辰海"]
source: chat_history
tags: ["屏幕共享", "Rooms版本", "下行网络", "视频质量"]
created: 2026-01-23
updated: 2026-03-15
---

## 问题：Rooms Rooms设备看不到特定用户的屏幕共享

## 问题详情

**现象**：
会议中某用户共享屏幕时，电脑端能看到但会议平板看不到共享内容，其他人共享时会议平板能正常看到

## 排查过程

1. 检查Rooms版本 → 发现不是最新2.2.2版本
2. 查看下行网络 → 拉到了最低档的流（马赛克）

## 问题原因

Rooms版本未更新到最新版本，且下行网络条件差导致拉到最低分辨率的流

## 解决方案

升级Rooms到最新2.2.2版本，检查网络条件
