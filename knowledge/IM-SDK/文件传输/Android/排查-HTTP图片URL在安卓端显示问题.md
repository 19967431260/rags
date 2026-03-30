---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 文件传输
platform: Android
title: HTTP图片URL在安卓端显示问题
root_cause: 安卓端限制了HTTP协议的图片访问，需要HTTPS
solution: 将图片URL的http改为https，或在安卓端配置允许HTTP访问
customers: ['杭州量子世界']
source: chat_history
tags: ['HTTP', 'HTTPS', '图片显示', 'Android']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Android HTTP图片URL在安卓端显示问题

## 问题详情

**现象**：
客户反馈后端上传的图片，安卓端显示不了，iOS端正常。

## 排查过程

1. 检查图片URL → http协议
2. 检查安卓限制 → 发现安卓限制了HTTP访问
3. 建议修改为HTTPS

## 问题原因

安卓端限制了HTTP协议的图片访问，需要HTTPS

## 解决方案

将图片URL的http改为https，或在安卓端配置允许HTTP访问

## 其他触发场景

（合并时在此处追加）
