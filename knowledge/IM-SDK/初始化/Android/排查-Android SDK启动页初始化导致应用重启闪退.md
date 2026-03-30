---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: Android SDK启动页初始化导致应用重启闪退
root_cause: SDK初始化放在启动页onCreate中，当应用因权限变更重启时，启动页重建过程中可能调用SDK接口时SDK尚未完成初始化
solution: 将SDK初始化代码从启动页onCreate移到Application中执行，确保应用启动时第一时间完成SDK初始化
customers: ['Melvo']
source: chat_history
tags: ['初始化', 'Android', '闪退', 'Application', '启动页']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：Android Android SDK启动页初始化导致应用重启闪退

## 问题详情

**现象**：
应用在启动页onCreate中初始化云信SDK，当用户去设置关闭权限后回到应用时，应用重启过程中直接闪退，报错SDK not initialized or invoked in wrong process。

## 排查过程

1. 客户反馈在启动页onCreate中初始化SDK
2. 问题出现在用户关闭权限后应用重启时
3. 经排查发现SDK在17:20:02:986才执行初始化，但在此之前已调用SDK接口
4. 接口调用时机问题：应用重启时启动页onCreate执行时机可能有问题
**关键发现**：初始化代码放在启动页onCreate中，当应用因权限变更重启时，启动页重建可能导致SDK未初始化就被调用

## 问题原因

SDK初始化放在启动页onCreate中，当应用因权限变更重启时，启动页重建过程中可能调用SDK接口时SDK尚未完成初始化

## 解决方案

将SDK初始化代码从启动页onCreate移到Application中执行，确保应用启动时第一时间完成SDK初始化

## 其他触发场景

（合并时在此处追加）
