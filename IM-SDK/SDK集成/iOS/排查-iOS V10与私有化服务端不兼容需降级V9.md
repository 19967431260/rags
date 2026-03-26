---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK集成
platform: iOS
title: iOS V10 SDK与私有化服务端不兼容需降级到V9
root_cause: 客户iOS App升级了SDK到V10，但私有化服务端不支持V10；V10客户端无法连接V9服务端
solution: iOS SDK降级到V9最新版本（pod指定NIMSDK_LITE版本9.20.12）；如已在线上用户中更新了V10，需要卸载重装；建议下次升级SDK前先确认服务端版本兼容性
customers: ["海思太科-云信rtc私有化"]
source: chat_history
tags: ["iOS", "V10", "私有化", "不兼容", "V9降级"]
created: 2025-07-08
updated: 2025-07-25
---

## 问题：iOS V10 SDK与私有化服务端不兼容需降级到V9

## 问题原因

客户iOS App升级了SDK到V10，但私有化服务端不支持V10；V10客户端无法连接V9服务端

## 解决方案

iOS SDK降级到V9最新版本（pod指定NIMSDK_LITE版本9.20.12）；如已在线上用户中更新了V10，需要卸载重装；建议下次升级SDK前先确认服务端版本兼容性
