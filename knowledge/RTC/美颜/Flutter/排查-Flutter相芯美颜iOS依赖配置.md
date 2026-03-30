---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 美颜
platform: Flutter
title: Flutter相芯美颜iOS依赖配置
root_cause: Podfile中的flutter_root路径配置不正确，使用了demo作者的固定路径
solution: 修改Podfile中的flutter_root为环境变量或本地Flutter实际路径：flutter_root = ENV['FLUTTER_ROOT'] || '/Users/username/flutter'
customers: ['南宁小清柠']
source: chat_history
tags: ['Flutter', '美颜', 'pod install', '路径配置', '相芯']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Flutter Flutter相芯美颜iOS依赖配置

## 问题详情

**现象**：
客户运行Flutter美颜demo时，pod install报错，路径配置问题。

## 排查过程

1. 检查Podfile中的flutter_root路径配置
2. 发现路径指向了demo作者的个人路径

## 问题原因

Podfile中的flutter_root路径配置不正确，使用了demo作者的固定路径

## 解决方案

修改Podfile中的flutter_root为环境变量或本地Flutter实际路径：flutter_root = ENV['FLUTTER_ROOT'] || '/Users/username/flutter'

## 其他触发场景

（合并时在此处追加）
