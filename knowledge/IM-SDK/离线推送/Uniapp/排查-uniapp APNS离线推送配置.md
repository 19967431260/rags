---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Uniapp
title: uniapp APNS离线推送配置
root_cause: 离线打包APP未直接使用hbuilder，导致推送token未正确上报
solution: 需要排查离线打包方式下推送token的获取和上报。接收方APP登录IM时，推送插件会调用系统方法获取推送token然后上报，云信服务端需要拿到设备的推送token才能调用厂商API进行推送。
customers: ["嘉立创"]
source: chat_history
tags: ["离线推送", "APNS", "uniapp", "推送token", "离线打包"]
created: 2025-05-07
updated: 2025-03-20
---

## 问题：Uniapp uniapp APNS离线推送配置

## 问题详情

**现象**：
uniapp配置APNS离线推送，按照配置流程设置后未收到推送。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Uniapp

## 排查过程

1. 确认Apple推送配置、网易云信配置、uniapp代码初始化配置、hbuildx插件配置流程
2. 查询服务端发现没有推送token
3. 确认接收方APP登录IM时推送插件会获取推送token并上报
4. 排查发现是离线打包APP，没有直接使用hbuilder导致token未上报

## 问题原因

离线打包APP未直接使用hbuilder，导致推送token未正确上报

## 解决方案

需要排查离线打包方式下推送token的获取和上报。接收方APP登录IM时，推送插件会调用系统方法获取推送token然后上报，云信服务端需要拿到设备的推送token才能调用厂商API进行推送。

## 其他触发场景

