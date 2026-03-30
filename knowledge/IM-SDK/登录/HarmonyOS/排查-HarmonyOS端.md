---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: HarmonyOS
title: HarmonyOS端190002非法状态错误
root_cause: 未登录成功就调用了SDK方法
solution: 确保先完成登录流程，登录成功后再调用其他SDK方法
customers: ["南京爱一格"]
source: chat_history
tags: ["190002", "illegal state", "登录", "HarmonyOS"]
created: 2025-02-12
updated: 2026-03-20
---

## 问题：HarmonyOS HarmonyOS端190002非法状态错误

## 问题详情

**现象**：
在鸿蒙平台调用SDK方法时返回190002错误码，提示illegal state非法状态。

## 排查过程

（从会话记录提取）

## 问题原因

未登录成功就调用了SDK方法

## 解决方案

确保先完成登录流程，登录成功后再调用其他SDK方法

## 其他触发场景
- [HarmonyOS] HarmonyOS端190002非法状态错误，来源：['南京爱一格']，2026-03-20
- [HarmonyOS] HarmonyOS端190002非法状态错误，来源：['南京爱一格']，2026-03-20

