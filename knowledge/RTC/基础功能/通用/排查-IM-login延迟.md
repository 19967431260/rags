---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 基础功能
platform: 通用
title: IM login方法延迟13秒
root_cause: "SDK进程被阻塞"
solution: "先观察，客户端阻塞服务器日志无法分析"
customers: ["SVIPS云信"]
source: chat_history
tags: []
created: 2025-06-27
updated: 2025-03-23
---

## 问题：IM login方法延迟13秒

## 问题详情

**现象**：
从调IM login方法到回调触发，中间间隔了大概13s左右。

**环境信息**：
- 平台：通用

## 排查过程

1. 查看日志 → SDK进程被阻塞，啥打印都没有
2. 进入后台才打印日志 → 阻塞期间无日志
3. 服务器日志分析 → 客户端发包逻辑延后

## 问题原因

SDK的进程被阻塞住了，直到进入后台才恢复。客户端一直阻塞，过了13s才触发后续逻辑执行到请求服务器。

## 解决方案

1. 先观察
2. 服务器日志无法分析（客户端阻塞导致）
3. 检查是否有main thread blocked记录

## 其他触发场景

