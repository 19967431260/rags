---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: vivo推送SDK版本过低导致收不到推送
root_cause: vivo推送SDK版本过低（3.0.0.0_480），建议升级到4.0.0.0_500
solution: 将vivo推送SDK从3.0.0.0_480升级到4.0.0.0_500版本。
customers: ['广西珍心传媒']
source: chat_history
tags: ['vivo推送', 'SDK版本', '3.0.0.0_480', '4.0.0.0_500']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Android vivo推送SDK版本过低导致收不到推送

## 问题详情

**现象**：
客户反馈vivo手机推送收不到，当前使用的是3.0.0.0_480版本。

## 排查过程

1. 客户反馈vivo推送收不到
2. 技术支持询问vivo推送SDK版本
3. 客户反馈版本为3.0.0.0_480
4. 技术支持建议升级到4.0.0.0_500版本
5. 客户升级后遇到AndroidManifest.xml中未配置local_iv错误
6. 最终客户自行解决vivo配置问题

## 问题原因

vivo推送SDK版本过低（3.0.0.0_480），建议升级到4.0.0.0_500

## 解决方案

将vivo推送SDK从3.0.0.0_480升级到4.0.0.0_500版本。

## 其他触发场景

（合并时在此处追加）
