---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 后台保活
platform: Uniapp
title: Uniapp切后台后长连接断开及重连问题
root_cause: uniapp等类webview框架在后台会阻塞JS执行并限制网络，导致长连接断开
solution: 1. 新版SDK已优化后台保活逻辑
2. 临时方案：回前台后若3秒未收到onConnectStatus，可重新初始化NIM
3. 或提供按钮让用户手动重连
customers: ["黄骅市达祥知识产权服务有限公司"]
source: chat_history
tags: ["IM-SDK", "Uniapp", "后台保活", "长连接", "protocol send failed"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Uniapp Uniapp切后台后长连接断开及重连问题

## 问题详情

**现象**：
App退入后台再进入前台时，出现protocol send failed错误，长连接断开导致查询失败，onLoginStatus监听不稳定。

## 排查过程

1. 客户反馈app切后台后再进入前台查询历史消息失败
2. 报错protocol send failed，长链接断开
3. onLoginStatus监听有时能触发有时不能
4. 原因是uniapp容器在后台会阻塞JS执行并限制网络
5. 新版SDK已优化此问题

## 问题原因

uniapp等类webview框架在后台会阻塞JS执行并限制网络，导致长连接断开

## 解决方案

1. 新版SDK已优化后台保活逻辑
2. 临时方案：回前台后若3秒未收到onConnectStatus，可重新初始化NIM
3. 或提供按钮让用户手动重连

## 其他触发场景

