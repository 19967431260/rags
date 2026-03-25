---
track_type: "排查类"
sub_type: "使用问题"
product: "Server SDK"
feature: "内存泄漏"
platform: "Server"
title: "server-sdk-java 1.1.1以下版本存在metrics组件内存泄漏"
root_cause: "server-sdk-java 1.1.1以下版本的metrics组件存在内存泄漏。"
solution: "建议尽快升级至server-sdk-java 1.1.1版本，该版本已修复metrics组件内存泄漏问题。"
customers: ["FVIP云信-时间在线-gj"]
source: "chat_history"
tags: ["server-sdk-java", "内存泄漏", "metrics", "升级", "1.1.1"]
created: "2025-09-18"
updated: "2026-03-20"
---

## 问题：Server server-sdk-java 1.1.1以下版本存在metrics组件内存泄漏

## 问题详情

**现象**：
server-sdk-java在使用im-v2-api场景下存在metrics组件内存泄漏问题，长时间运行后可能影响服务稳定性。

## 问题原因

server-sdk-java 1.1.1以下版本的metrics组件存在内存泄漏。

## 解决方案

建议尽快升级至server-sdk-java 1.1.1版本，该版本已修复metrics组件内存泄漏问题。

## 其他触发场景
