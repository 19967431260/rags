---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成配置
platform: Uniapp
title: IM分包加载配置引用不到工具方法
root_cause: 分包加载时路径问题导致无法引用主包utils
solution: 将相关配置和工具方法调整位置，确保分包可以访问到必要的工具方法
customers: ['河南寻到智能科技有限公司']
source: chat_history
tags: ['Uniapp', '分包', '配置', '工具方法', '引用']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp IM分包加载配置引用不到工具方法

## 问题详情

**现象**：
IM配置放在主包，小程序页面放在分包，导致引用不到utils下的工具方法。

## 排查过程



## 问题原因

分包加载时路径问题导致无法引用主包utils

## 解决方案

将相关配置和工具方法调整位置，确保分包可以访问到必要的工具方法

## 其他触发场景

（合并时在此处追加）
