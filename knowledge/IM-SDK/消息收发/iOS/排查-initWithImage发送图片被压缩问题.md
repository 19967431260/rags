---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: iOS
title: initWithImage发送图片被压缩问题
root_cause: initWithImage方法会做格式转换以防止其他端兼容问题，导致图片被压缩
solution: 使用initWithFilepath方法发送图片，避免格式转换导致的压缩
customers: ['杭州跨客技术服务有限公司']
source: chat_history
tags: ['initWithImage', '图片压缩', 'initWithFilepath', 'iOS']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：iOS initWithImage发送图片被压缩问题

## 问题详情

**现象**：
客户使用initWithImage方法发送图片，设置压缩质量为1.0，但下载下来的图片仍被压缩。

## 排查过程

1. 检查图片URL → 正常
2. 对比原图和发送后图片 → 确认发送前被压缩
3. 确认initWithImage会做格式转换

## 问题原因

initWithImage方法会做格式转换以防止其他端兼容问题，导致图片被压缩

## 解决方案

使用initWithFilepath方法发送图片，避免格式转换导致的压缩

## 其他触发场景

（合并时在此处追加）
