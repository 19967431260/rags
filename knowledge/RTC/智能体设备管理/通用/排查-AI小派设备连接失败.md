---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 智能体设备管理
platform: 通用
title: AI小派设备连接失败
root_cause: 小派AI小程序目前只支持云信自己的appkey，客户使用自己的appkey无法连接
solution: 登录智能体控制台(https://rtc-agent-console.netease.im)，在设备管理中手动绑定设备ID(90:70:69:32:d9:18)
customers: ["晨芯成科技"]
source: chat_history
tags: ["AI小派", "设备连接", "appkey", "智能体控制台"]
created: 2026-02-27
updated: 2026-03-17
---

## 问题：通用 AI小派设备连接失败

## 问题详情

**现象**：
使用GitHub上的demo对接AI小派，小程序上输入激活码和WiFi配置成功，但设备一直连接不上，日志循环打印相同内容。

## 排查过程

1. 检查日志打印 → 发现日志循环打印
2. 检查appkey配置 → 发现使用的是客户自己的appkey

**关键发现**：小派AI小程序目前只支持云信自己的appkey

## 问题原因

小派AI小程序目前只支持云信自己的appkey，客户使用自己的appkey无法连接

## 解决方案

登录智能体控制台(https://rtc-agent-console.netease.im)，在设备管理中手动绑定设备ID(90:70:69:32:d9:18)

## 其他触发场景
