---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 推流拉流
platform: 微信小程序
title: 微信小程序RTC推流失败operateXWebLivePusher:fail:internal error
root_cause:
solution: 需在微信公众平台 → 功能 → 直播/实时音视频中开通相应功能。同时确保subscribe方法拿到的拉流URL正确放到player组件中。
customers: ["黑龙江景佑医疗器械"]
source: chat_history
tags: ["推流", "拉流", "微信小程序", "operateXWebLivePusher", "功能开通"]
created: 2026-02-11
updated: 2026-03-17
---

## 问题：微信小程序 微信小程序RTC推流失败operateXWebLivePusher:fail:internal error

## 问题详情

**现象**：
微信小程序RTC初始化成功，用户加入同一房间，但推流拉流功能不生效，双方画面无法显示。本地视频画面能看见，但报错operateXWebLivePusher:fail:internal error。

## 排查过程

1. 检查publish方法是否拿到推流URL → 已拿到
2. 检查本地视频画面 → 能看见
3. 检查subscribe方法是否拿到拉流URL → 待确认
4. 检查域名白名单配置 → 已配置
5. 检查微信公众平台功能开通 → 待确认直播/实时音视频功能是否开通

## 问题原因



## 解决方案

需在微信公众平台 → 功能 → 直播/实时音视频中开通相应功能。同时确保subscribe方法拿到的拉流URL正确放到player组件中。

## 其他触发场景
