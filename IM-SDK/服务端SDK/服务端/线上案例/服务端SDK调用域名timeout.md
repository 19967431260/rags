---
track_type: 排查类
sub_type: 线上事故
product: IM-SDK
feature: 服务端SDK
platform: 服务端
title: 服务端SDK调用域名timeout
root_cause: 服务器受到攻击，存在个别极少数请求超时
solution: SDK会自动选择其他入口的域名，理论上不会有很大影响。
customers: ["深圳富旅奇缘"]
source: chat_history
tags: ["IM", "服务端SDK", "timeout", "域名"]
created: 2025-05-08
updated: 2025-03-20
---

## 问题：服务端 服务端SDK调用域名timeout

## 问题详情

**现象**：
使用serverSDK调用api-cn-01.yunxinapi.com出现timeout异常。

## 排查过程

**关键发现**：服务器受到攻击，存在个别极少数请求超时

## 问题原因

服务器受到攻击，存在个别极少数请求超时

## 解决方案

SDK会自动选择其他入口的域名，理论上不会有很大影响。
