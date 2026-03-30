---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: TypeScript配置
platform: Web
title: UIKit TypeScript项目allowJs配置
root_cause: TypeScript默认不处理.js文件，需要启用allowJs选项
solution: 在tsconfig.json的compilerOptions下添加allowJs: true，允许TypeScript处理.js文件
customers: ['千寻代售APP沟通群']
source: chat_history
tags: ['UIKit', 'TypeScript', 'allowJs', '打包错误']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Web UIKit TypeScript项目allowJs配置

## 问题详情

**现象**：
客户按照文档打包UIKit项目时报错，提示TypeScript无法处理.js文件。

## 排查过程



## 问题原因

TypeScript默认不处理.js文件，需要启用allowJs选项

## 解决方案

在tsconfig.json的compilerOptions下添加allowJs: true，允许TypeScript处理.js文件

## 其他触发场景

（合并时在此处追加）
