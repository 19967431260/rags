---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: HarmonyOS
title: 切换账号后使用旧会话ID导致参数错误
root_cause: 用户退出登录后，业务层未清理旧账号的会话数据，新账号登录后界面仍展示并使用旧账号的conversationId。
solution: 切换账号时需清理业务层缓存的旧账号会话数据，确保新账号登录后使用正确的会话ID。SDK侧调用logout即可，但业务层需同步清理界面数据。
customers: ["FVIP-云信-上海麦色"]
source: chat_history
tags: ["HarmonyOS", "参数错误", "切换账号", "conversationId", "logout"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：HarmonyOS 切换账号后使用旧会话ID导致参数错误

## 问题详情

**现象**：
鸿蒙SDK中偶发报参数错误，同样的参数有时成功有时失败。客户退出A账号登录B账号后，界面仍展示并使用A账号的conversationId查询会话。

## 排查过程

1. 查看错误日志 → 发现使用A账号登录，却用B账号开头的会话id查询
**关键发现**：用户退出登录后，业务层未清理旧账号的会话数据，导致新账号使用了错误的会话ID

## 问题原因

用户退出登录后，业务层未清理旧账号的会话数据，新账号登录后界面仍展示并使用旧账号的conversationId。

## 解决方案

切换账号时需清理业务层缓存的旧账号会话数据，确保新账号登录后使用正确的会话ID。SDK侧调用logout即可，但业务层需同步清理界面数据。

## 其他触发场景

