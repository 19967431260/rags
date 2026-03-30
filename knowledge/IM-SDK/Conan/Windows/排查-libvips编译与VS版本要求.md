---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Conan
platform: Windows
title: libvips编译与VS版本要求
root_cause: libvips 8.15以上版本要求VS工具链192以上(VS 2019+)，VS 2017不兼容。8.16.0官方未同步到Conan Center
solution: 使用VS 2022可以编译libvips 8.15.3。如需8.16.0可clone官方配方工程本地创建版本
customers: ['VIP云信-广州敬汕贸易有限公司']
source: chat_history
tags: ['Conan', 'libvips', 'VS2022', '编译']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：Windows libvips编译与VS版本要求

## 问题详情

**现象**：
使用Conan安装libvips 8.15.x出现libjpeg冲突，8.16.0拉取不到

## 排查过程

1. 检查Conan Center → 8.16.0未同步
2. 测试8.15.x → 发现需要VS 2019以上
3. 尝试VS 2022 → 8.15.3编译通过

## 问题原因

libvips 8.15以上版本要求VS工具链192以上(VS 2019+)，VS 2017不兼容。8.16.0官方未同步到Conan Center

## 解决方案

使用VS 2022可以编译libvips 8.15.3。如需8.16.0可clone官方配方工程本地创建版本

## 其他触发场景

（合并时在此处追加）
