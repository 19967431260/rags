---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Conan
platform: Windows
title: Conan编译Python版本兼容问题
root_cause: Python 3.13与Conan的meson工具链存在兼容性问题，isabs函数行为变化
solution: 使用Python 3.12.x版本进行Conan编译，避免使用3.13
customers: ['VIP云信-广州敬汕贸易有限公司']
source: chat_history
tags: ['Conan', 'Python', 'meson', '编译', '3.13']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Windows Conan编译Python版本兼容问题

## 问题详情

**现象**：
使用Python 3.13编译时出现meson路径问题，lcms编译失败

## 排查过程

1. 检查错误日志 → 发现meson路径判断问题
2. 对比Python版本 → 3.13出现isabs问题
3. 尝试Python 3.12 → 编译通过

## 问题原因

Python 3.13与Conan的meson工具链存在兼容性问题，isabs函数行为变化

## 解决方案

使用Python 3.12.x版本进行Conan编译，避免使用3.13

## 其他触发场景

（合并时在此处追加）
