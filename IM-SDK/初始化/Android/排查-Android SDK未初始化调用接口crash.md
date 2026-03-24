---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: Android SDK未初始化调用接口crash
root_cause: push进程在Application启动时可能提前触发，此时SDK尚未初始化。
solution: 确保SDK初始化在Application中完成，或在调用SDK接口前判断初始化状态。push进程是云信内部进程，需保证在主进程中完成初始化。
customers: ['北京四维云信']
source: chat_history
tags: ['crash', '初始化', 'push进程', 'Android', '主进程']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Android Android SDK未初始化调用接口crash

## 问题详情

**现象**：
客户将初始化移到MainActivity的onCreate后，出现未初始化就调用接口导致的crash。

## 排查过程

1. 分析crash日志发现是push进程触发；2. 确认初始化代码位置；3. 发现push进程提前调用了SDK接口。

## 问题原因

push进程在Application启动时可能提前触发，此时SDK尚未初始化。

## 解决方案

确保SDK初始化在Application中完成，或在调用SDK接口前判断初始化状态。push进程是云信内部进程，需保证在主进程中完成初始化。

## 其他触发场景

（合并时在此处追加）
