---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录认证
platform: Android
title: IM初始化时登录失败无回调
root_cause: 初始化时自动登录可能因网络等原因失败，但无回调通知
solution: init时先不传logininfo（传null），初始化完成后在activity里手动调用login接口，实现回调监听登录状态
customers: ['江西闪招信息技术有限公司']
source: chat_history
tags: ['登录', 'init', 'logininfo', '回调', '手动登录']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android IM初始化时登录失败无回调

## 问题详情

**现象**：
IM初始化时传入logininfo，有时登录成功有时失败，且不触发登录失败回调。

## 排查过程



## 问题原因

初始化时自动登录可能因网络等原因失败，但无回调通知

## 解决方案

init时先不传logininfo（传null），初始化完成后在activity里手动调用login接口，实现回调监听登录状态

## 其他触发场景

（合并时在此处追加）
