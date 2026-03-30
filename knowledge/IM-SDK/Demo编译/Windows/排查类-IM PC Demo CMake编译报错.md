---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Demo编译
platform: Windows
title: IM PC Demo CMake编译报错
root_cause: Conan版本不支持VS2022的MSVC编译器版本1942
solution: 使用develop分支版本，已提交修复支持VS2022 1942版本
customers: ['广州群市网络科技有限公司']
source: chat_history
tags: ['IM V9', 'Windows', 'CMake', 'Conan', 'VS2022']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：IM PC Demo CMake编译报错

## 问题详情

**现象**：
客户使用VS2022编译IM PC Demo时，CMake与Conan集成报错，提示Unknown MSVC compiler version

## 排查过程

1. 客户执行cmake报错
2. 错误显示Conan无法识别MSVC编译器版本19.42
3. 建议升级Conan版本
4. 研发在develop分支提交修复

## 问题原因

Conan版本不支持VS2022的MSVC编译器版本1942

## 解决方案

使用develop分支版本，已提交修复支持VS2022 1942版本

## 其他触发场景

（合并时在此处追加）
