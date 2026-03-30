---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 日志管理
platform: Android
title: SDK日志裁剪策略与存储路径导致日志丢失
root_cause: 1. sdkStorageRootPath配置在cache目录，用户使用清理工具时会删除缓存内容
2. V9版本日志按文件大小裁剪，裁剪位置随机
solution: 1. 避免将sdkStorageRootPath配置到cache目录，改用files目录
2. 升级到V10版本，新版本采用按天存储策略，不会有日志裁剪问题
3. 如暂时无法升级V10，可先保持V9接口升级到V10 SDK
customers: ["VIP云信-广州心晴"]
source: chat_history
tags: ["日志裁剪", "cache目录", "sdkStorageRootPath", "按天存储", "V10升级"]
created: 2026-02-25
updated: 2026-03-15
---

## 问题：Android SDK日志裁剪策略与存储路径导致日志丢失

## 问题详情

**现象**：
客户发现SDK日志只保留当天数据，大小与文档描述的裁剪策略不符。日志配置在cache目录，用户清理缓存时会删除日志内容。

## 排查过程

1. 检查日志大小 → 只有当天数据
2. 检查日志起始位置 → 从初始化日志开始，说明是新安装或被清理
3. 检查存储路径 → 配置在cache目录

## 问题原因

1. sdkStorageRootPath配置在cache目录，用户使用清理工具时会删除缓存内容
2. V9版本日志按文件大小裁剪，裁剪位置随机

## 解决方案

1. 避免将sdkStorageRootPath配置到cache目录，改用files目录
2. 升级到V10版本，新版本采用按天存储策略，不会有日志裁剪问题
3. 如暂时无法升级V10，可先保持V9接口升级到V10 SDK
