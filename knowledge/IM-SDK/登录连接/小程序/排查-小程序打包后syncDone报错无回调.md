---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录连接
platform: 小程序
title: 小程序打包后syncDone报错无回调
root_cause: 登录成功情况下再次调用connect会导致报错
solution: 检查connect方法的调用位置，避免在已登录状态下重复调用connect。
customers: ["智联招聘"]
source: chat_history
tags: ["syncDone", "connect", "重复调用", "小程序"]
created: 2025-02-07
updated: 2025-03-20
---

## 问题：小程序 小程序打包后syncDone报错无回调

## 问题详情

**现象**：
小程序打包后获取IM聊天详情出现异常，执行syncDone时报错且没有收到回调。

**环境信息**：
- 平台：小程序

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 询问调用方法 → syncDone事件
2. 收集console日志分析
3. 打开SDK debug模式收集详细日志
4. 分析日志发现connect方法重复调用

**关键发现**：登录成功情况下再次调用connect会导致报错

## 问题原因

登录成功情况下再次调用connect会导致报错。

## 解决方案

检查connect方法的调用位置，避免在已登录状态下重复调用connect。

## 其他触发场景
