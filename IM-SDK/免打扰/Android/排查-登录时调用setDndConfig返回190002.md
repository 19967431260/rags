---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 免打扰
platform: Android
title: 登录时调用setDndConfig返回190002
root_cause: setDndConfig调用时还没登录完成
solution: 设置免打扰等需要协议交互的操作,都建议等数据同步完成后再调用
customers: ["WooPlus"]
source: chat_history
tags: ["190002","setDndConfig","登录","数据同步"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：Android 登录时调用setDndConfig返回190002

## 问题详情

**现象**：
登录后等主数据同步完成后调用setDndConfig设置免打扰,返回190002错误码

## 排查过程

1. 检查日志 → 发现setDndConfig调用时还在登录过程中,还没登录完成

**关键发现**: 调用时机过早,需要等登录完成

## 问题原因

setDndConfig调用时还没登录完成

## 解决方案

设置免打扰等需要协议交互的操作,都建议等数据同步完成后再调用

## 其他触发场景

