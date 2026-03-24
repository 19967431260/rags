---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录登出
platform: HarmonyOS
title: HarmonyOS切换账号登录提示App Key不存在
root_cause: 客户项目中的登录登出逻辑问题，非法状态是由于未登录成功时调用退出引起
solution: 对照demo检查登录登出逻辑，确保正确的调用顺序
customers: ['南京爱一格']
source: chat_history
tags: ['登录', '登出', 'App Key', 'HarmonyOS', '切换账号']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：HarmonyOS HarmonyOS切换账号登录提示App Key不存在

## 问题详情

**现象**：
客户登出后重新登录时，提示App Key不存在错误。

## 排查过程

1. 客户检查登出和登录代码逻辑
2. 技术支持提供demo测试
3. 在demo上测试正常

## 问题原因

客户项目中的登录登出逻辑问题，非法状态是由于未登录成功时调用退出引起

## 解决方案

对照demo检查登录登出逻辑，确保正确的调用顺序

## 其他触发场景

（合并时在此处追加）
