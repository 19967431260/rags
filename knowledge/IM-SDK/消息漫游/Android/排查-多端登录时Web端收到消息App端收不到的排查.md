---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息漫游
platform: Android
title: 多端登录时Web端收到消息App端收不到的排查
root_cause: 发送端设置roamingEnabled=false（消息不漫游），Web端先收到消息后，App重连无法获取漫游消息；同时App切后台后被系统回收无法收到通知
solution: 1. 发送消息时设置NIMMessageSetting.roamingEnabled=true开启漫游；2. App切后台需对接厂商推送才能收到离线通知；参考离线推送集成文档
customers: ["淮南东东网络科技有限公司"]
source: chat_history
tags: ["漫游","多端登录","自定义消息","Electron","离线推送"]
created: 2025-07-31
updated: 2026-03-26
---

## 问题：Android 多端登录时Web端收到消息App端收不到的排查

## 问题详情

**现象**：
Web端（Electron）和App同时在线时，Web收到自定义消息，但App收不到；App先收到过漫游消息后就没再收到

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：Web端（Electron）和App同时在线

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认收发双方账号和appkey → 确认环境配置正常
2. 检查发送端配置：发现发送时设置了漫游关闭 → 发现漫游开关被关闭
3. 确认App是否正确对接了厂商推送 → App未正确对接厂商推送

**关键发现**：发送端设置roamingEnabled=false导致消息不漫游，Web端先收到后App无法获取

## 问题原因

发送端设置roamingEnabled=false（消息不漫游），Web端先收到消息后，App重连无法获取漫游消息；同时App切后台后被系统回收无法收到通知

## 解决方案

1. 发送消息时设置NIMMessageSetting.roamingEnabled=true开启漫游
2. App切后台需对接厂商推送才能收到离线通知；参考离线推送集成文档

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
