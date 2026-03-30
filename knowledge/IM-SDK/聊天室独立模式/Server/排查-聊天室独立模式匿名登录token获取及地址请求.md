---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "聊天室独立模式"
platform: "Server"
title: "聊天室独立模式匿名登录token获取及地址请求"
root_cause: "服务端获取聊天室地址时clienttype选择错误"
solution: "1. 匿名登录token随便传值即可；2. 聊天室地址需要通过服务端API请求；3. 获取地址时注意选择正确的clienttype（Web端选1，Android/iOS选2）"
customers: ["智己"]
source: "chat_history"
tags: ["聊天室", "独立模式", "匿名登录", "token", "clienttype"]
created: "2025-09-25"
updated: "2026-03-20"
---

## 问题：Server 聊天室独立模式匿名登录token获取及地址请求

## 问题详情

**现象**：
咨询聊天室登录独立模式下匿名登录的token如何获取，以及聊天室地址获取方式

## 排查过程

1. 确认token获取方式 → 匿名登录token随便传一个值即可，不会校验
2. 确认地址获取方式 → 需要通过服务端API请求
3. 排查连接超时问题 → 连接地址获取时clienttype选择有误
**关键发现**：服务端获取地址时clienttype需要选择正确

## 问题原因

服务端获取聊天室地址时clienttype选择错误

## 解决方案

1. 匿名登录token随便传值即可；2. 聊天室地址需要通过服务端API请求；3. 获取地址时注意选择正确的clienttype（Web端选1，Android/iOS选2）

## 其他触发场景
