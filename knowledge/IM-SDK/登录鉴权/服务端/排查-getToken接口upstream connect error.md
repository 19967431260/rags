---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 登录鉴权
platform: 服务端
title: getToken接口upstream connect error
root_cause: 客户环境无法访问公网地址api.netease.im
solution: 确认api.netease.im为公网地址，需检查客户网络环境是否能访问公网
customers: ['拍拍贷']
source: chat_history
tags: ['getToken', 'connection failure', '公网', '网络']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：服务端 getToken接口upstream connect error

## 问题详情

**现象**：
调用http://api.netease.im/nimserver/user/getToken.action接口异常，报错upstream connect error or disconnect/reset before headers. reset reason: connection failure

## 排查过程

1. 询问是否能ping通 → 客户确认是公网地址问题
2. 客户自行定位 → 确认是公网访问问题

## 问题原因

客户环境无法访问公网地址api.netease.im

## 解决方案

确认api.netease.im为公网地址，需检查客户网络环境是否能访问公网

## 其他触发场景

（合并时在此处追加）
