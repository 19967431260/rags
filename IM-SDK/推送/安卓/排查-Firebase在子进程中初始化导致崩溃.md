---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: 安卓
title: Firebase在子进程中初始化导致崩溃
root_cause: 与aab打包、gradle shrinkResources配置相关，可能资源被压缩导致问题
solution: 问题仍在排查中，建议检查gradle配置中shrinkResources和minifyEnabled设置，或提供完整logcat日志进一步分析
customers: ['FVIP云信-时间在线-gj']
source: chat_history
tags: ['Firebase', '崩溃', '子进程', 'Application', 'aab', 'shrinkResources']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：安卓 Firebase在子进程中初始化导致崩溃

## 问题详情

**现象**：
Android应用集成Firebase后发生闪退，客户反馈初始化代码已放在Application中但仍崩溃。

**环境信息**：
- 平台：安卓
- 产品：IM-SDK

## 排查过程

1. 初步判断Firebase需在子进程初始化
2. 客户反馈没有其他进程
3. 建议放在Application.onCreate初始化
4. 问题仍未解决，需进一步排查
5. 发现只有新注册用户有问题，旧账号正常
6. 发现只有aab转出的apk有问题，直接编译的apk正常
7. 发现与gradle设置shrinkResources有关

## 问题原因

与aab打包、gradle shrinkResources配置相关，可能资源被压缩导致问题

## 解决方案

问题仍在排查中，建议检查gradle配置中shrinkResources和minifyEnabled设置，或提供完整logcat日志进一步分析

## 其他触发场景

（合并时在此处追加）
