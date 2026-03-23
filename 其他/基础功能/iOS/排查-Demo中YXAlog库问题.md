---
track_type: 排查类
sub_type: Demo问题
product: 其他
feature: 基础功能
platform: iOS
title: Demo中YXAlog库问题
root_cause: YXAlog库与项目配置不兼容
solution: 升级到新版本或在Podfile中添加bitcode_strip脚本
customers:
  - 时间在线
source: chat_history
tags:
  - 证书
created: 2025-06-06
updated: 2025-03-23
---

## 问题：Demo中YXAlog库问题

## 问题详情

**现象**：
Demo项目中YXAlog库导致编译/上传问题。

## 问题原因

YXAlog库与项目配置不兼容。

## 解决方案

1. 升级到新版本（已去掉YXAlog库）
2. 或在Podfile中添加post_install脚本对YXAlog进行bitcode_strip处理

## 其他触发场景
