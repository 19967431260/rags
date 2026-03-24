---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息监听
platform: Android
title: observeRevokeMessage回调收不到
root_cause: 安卓监听放在登录后，登录成功到监听成功存在gap，可能漏掉回调
solution: 安卓监听尽量放在登录前，避免登录成功到监听成功之间的gap导致漏回调
customers: ['VIP云信_初晴_核芯']
source: chat_history
tags: ['observeRevokeMessage', '撤回消息', '监听', 'Android']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Android observeRevokeMessage回调收不到

## 问题详情

**现象**：
安卓SDK 9.14.4，在线状态下收不到消息撤回回调observeRevokeMessage

## 排查过程

1. 确认在线状态 → 在线
2. 确认监听时机 → 建议放在登录前监听
3. 分析原因 → 登录成功到监听成功有一段极小的gap，可能出现漏的情况

## 问题原因

安卓监听放在登录后，登录成功到监听成功存在gap，可能漏掉回调

## 解决方案

安卓监听尽量放在登录前，避免登录成功到监听成功之间的gap导致漏回调

## 其他触发场景

（合并时在此处追加）
