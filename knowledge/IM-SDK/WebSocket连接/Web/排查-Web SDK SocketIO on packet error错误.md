---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "WebSocket连接"
platform: "Web"
title: "Web SDK SocketIO on packet error错误"
root_cause: "网络异常导致socket断开"
solution: "1. 该错误一般因网络异常导致socket断开，会触发ondisconnect回调
2. 建议升级SDK到最新版本9.20.15
3. SDK下载地址：https://www.npmjs.com/package/@yxim/nim-web-sdk"
customers: ["SI云信-顺丰科技-小哥在线项目"]
source: "chat_history"
tags: ["WebSDK", "SocketIO", "on packet error", "网络异常", "V9"]
created: "2025-09-11"
updated: "2026-03-20"
---

## 问题：Web Web SDK SocketIO on packet error错误

## 问题详情

**现象**：
客户使用NIM_Web_SDK_rn_v9.0.1.js，在线上环境看到错误上报SocketIO on packet error，询问原因。

## 排查过程

1. 客户反馈只有错误上报，其他信息无
2. 技术支持判断一般是网络异常导致socket断开
3. 会回调ondisconnect
4. 建议升级到最新版本9.20.15

## 问题原因

网络异常导致socket断开

## 解决方案

1. 该错误一般因网络异常导致socket断开，会触发ondisconnect回调
2. 建议升级SDK到最新版本9.20.15
3. SDK下载地址：https://www.npmjs.com/package/@yxim/nim-web-sdk

## 其他触发场景
