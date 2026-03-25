---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录认证
platform: Flutter
title: iOS Flutter SDK崩溃问题
root_cause: nim_core 1.7.8版本的已知问题
solution: 升级到nim_core 1.9.0版本，该版本底层NIMSDK已修复此问题。
customers: ["广州还行科技有限公司"]
source: chat_history
tags: ["iOS", "Flutter", "崩溃", "CredentialHolder", "版本升级"]
created: 2025-05-30
updated: 2025-03-20
---

## 问题：Flutter iOS Flutter SDK崩溃问题

## 问题详情

**现象**：
客户反馈iOS上有少量崩溃，崩溃发生在yunxin__CredentialHolder__OnCredentialWillExpire。

## 排查过程

**关键发现**：nim_core 1.7.8版本的已知问题

## 问题原因

nim_core 1.7.8版本的已知问题

## 解决方案

升级到nim_core 1.9.0版本，该版本底层NIMSDK已修复此问题。
