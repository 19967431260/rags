---
track_type: 排查类
sub_type: 易用性问题
product: IM-SDK
feature: 鸿蒙SDK
platform: HarmonyOS
title: 鸿蒙SDK断网后登录失败回调问题
root_cause: 鸿蒙系统自身网络回调可能不准确，SDK保持不断重试逻辑
solution: 目前保持正常重试逻辑处理，等待鸿蒙系统更稳定后再评估优化方案
customers: ['ISV云信私有化-顺丰科技-多项目']
source: chat_history
tags: ['鸿蒙', '断网', '登录回调', '重试机制']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙SDK断网后登录失败回调问题

## 问题详情

**现象**：
客户反馈鸿蒙SDK在登录成功后断网，SDK会触发重试，但重试完成后没有收到ConnectFailed或LoginFailed回调。

## 排查过程

1. 客户测试登录成功后断网场景
2. 发现断网后SDK不断重试，约几秒一次，10次后都没有回调
3. 技术支持确认鸿蒙目前网络回调可能不准确
4. 目前保持正常重试逻辑，等鸿蒙系统更稳定后再优化

## 问题原因

鸿蒙系统自身网络回调可能不准确，SDK保持不断重试逻辑

## 解决方案

目前保持正常重试逻辑处理，等待鸿蒙系统更稳定后再评估优化方案

## 其他触发场景

（合并时在此处追加）
