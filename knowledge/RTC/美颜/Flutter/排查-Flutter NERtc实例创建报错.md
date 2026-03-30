---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 美颜
platform: Flutter
title: Flutter NERtc实例创建报错
root_cause: 项目中缺少相芯美颜的iOS依赖配置
solution: 参考相芯仓库示例引入iOS依赖：https://github.com/Faceunity/FUNeRTCFlutter
customers: ['南宁小清柠']
source: chat_history
tags: ['NERtc', '美颜', 'Flutter', 'iOS依赖', '相芯']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Flutter Flutter NERtc实例创建报错

## 问题详情

**现象**：
客户将demo的call.dart引入自己项目后，创建NERtc实例报错。

## 排查过程

1. 对比demo和项目代码
2. 发现缺少相芯美颜iOS依赖

## 问题原因

项目中缺少相芯美颜的iOS依赖配置

## 解决方案

参考相芯仓库示例引入iOS依赖：https://github.com/Faceunity/FUNeRTCFlutter

## 其他触发场景

（合并时在此处追加）
