---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: MultiDex
platform: Android
title: Release包MultiDex类找不到错误
root_cause: 疑似MultiDex配置问题，需进一步排查确认
solution: 按Android官方MultiDex文档检查配置：1. multiDexEnabled true 2. 替换Application为MultiDexApplication 3. attachBaseContext中调用MultiDex.install
customers: ['太旗富鑫']
source: chat_history
tags: ['Android', 'MultiDex', 'Release包', '类找不到', 'InitializationProvider', '混淆']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Release包MultiDex类找不到错误

## 问题详情

**现象**：
Android项目构建release包后打开报错，提示InitializationProvider类找不到，debug包正常。

## 排查过程

1. 客户反馈release包报错类找不到
2. 确认客户开启了混淆，检查混淆规则已添加
3. 查看mapping文件确认类未被混淆
4. 检查dex文件确认类存在
5. 确认MultiDex.install在attachBaseContext中调用
6. 建议关闭混淆测试
7. 建议按Android官方文档对比MultiDex配置

## 问题原因

疑似MultiDex配置问题，需进一步排查确认

## 解决方案

按Android官方MultiDex文档检查配置：1. multiDexEnabled true 2. 替换Application为MultiDexApplication 3. attachBaseContext中调用MultiDex.install

## 其他触发场景

（合并时在此处追加）
