---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 推拉流
platform: Uniapp
title: Uniapp小程序推拉流黑屏
root_cause: 小程序未开通live-pusher和live-player权限,且Uniapp中live-pusher组件不支持autopush参数
solution: 1. 配置小程序白名单：https://doc.yunxin.163.com/nertc/guide/jMzNzY2OTI?platform=miniProgram#配置白名单 2. 开通live-pusher和live-player权限 3. 使用手动推流模式,不使用自动推流
customers:
- 南通英可达信息技术有限公司
source: chat_history
tags:
- RTC
- Uniapp
- 小程序
- 黑屏
- live-pusher
- live-player
- 权限
- autopush
created: '2026-02-25'
updated: '2026-03-16'
---

## 问题：Uniapp Uniapp小程序推拉流黑屏

## 问题详情

**现象**：
Uniapp集成RTC SDK在小程序真机调试时,推流和拉流都黑屏,事件已收到并设置,但live-pusher和live-player的statechange和netstatus回调都没有触发。

## 排查过程

1. 检查事件回调 → 发现statechange和netstatus都没有回调
2. 检查白名单配置 → 发现未配置小程序白名单
3. 检查live-pusher和live-player权限 → 发现权限未开通

**关键发现**：小程序必须开通live-pusher和live-player权限才能推拉流,且Uniapp的live-pusher组件未定义autopush参数

## 问题原因

小程序未开通live-pusher和live-player权限,且Uniapp中live-pusher组件不支持autopush参数

## 解决方案

1. 配置小程序白名单：https://doc.yunxin.163.com/nertc/guide/jMzNzY2OTI?platform=miniProgram#配置白名单 2. 开通live-pusher和live-player权限 3. 使用手动推流模式,不使用自动推流
