---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: UI组件
platform: iOS
title: 呼叫组件工具栏hidden设置不生效问题
root_cause: operationView是根据呼叫状态动态隐藏显示的，直接设置hidden无法生效
solution: 需要源码引入，修改NECallViewController中的operationView显示逻辑，根据呼叫状态动态控制
customers: ["山东中时通"]
source: chat_history
tags: ["工具栏", "hidden", "自定义UI", "源码修改"]
created: 2025-02-07
updated: 2026-03-20
---

## 问题：iOS 呼叫组件工具栏hidden设置不生效问题

## 问题详情

**现象**：
客户自定义通话页面时，设置工具栏hidden无法隐藏，音频和视频呼叫都存在此问题。

## 排查过程

1. 客户提供复现demo → 确认问题存在
2. 排查代码 → operationView在NECallViewController类中动态添加，根据呼叫状态控制显示隐藏

## 问题原因

operationView是根据呼叫状态动态隐藏显示的，直接设置hidden无法生效

## 解决方案

需要源码引入，修改NECallViewController中的operationView显示逻辑，根据呼叫状态动态控制

## 其他触发场景

