---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化配置
platform: HarmonyOS
title: 鸿蒙端私有化配置方式与Web端差异
root_cause: 鸿蒙端私有化配置需要使用Web端的配置文件，与Android配置方式不同。
solution: 鸿蒙端使用Web端配置文件，通过initializeOptions中的loginServiceConfig配置lbsUrls和linkUrl，NIMHttpServiceConfig配置上传域名，NIMStorageServiceConfig配置下载域名。
customers: ['圆通']
source: chat_history
tags: ['鸿蒙', '私有化', '配置', '初始化', 'HarmonyOS']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙端私有化配置方式与Web端差异

## 问题详情

**现象**：
客户询问鸿蒙端私有化配置应该使用哪个配置文件，以及如何配置。

## 排查过程

1. 确认鸿蒙端使用Web端配置文件
2. 检查lbsUrls、linkUrl等配置项
3. 对比Android和鸿蒙配置差异

## 问题原因

鸿蒙端私有化配置需要使用Web端的配置文件，与Android配置方式不同。

## 解决方案

鸿蒙端使用Web端配置文件，通过initializeOptions中的loginServiceConfig配置lbsUrls和linkUrl，NIMHttpServiceConfig配置上传域名，NIMStorageServiceConfig配置下载域名。

## 其他触发场景

（合并时在此处追加）
