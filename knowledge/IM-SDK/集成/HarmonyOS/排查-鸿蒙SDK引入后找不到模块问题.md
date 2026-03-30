---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: HarmonyOS
title: 鸿蒙SDK引入后找不到模块问题
root_cause: 引入SDK后需要执行ohpm install安装依赖
solution: 执行ohpm install命令安装模块依赖
customers: ['杭州飓风网络有限公司']
source: chat_history
tags: ['鸿蒙', 'HarmonyOS', 'ohpm', '模块引入']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙SDK引入后找不到模块问题

## 问题详情

**现象**：
客户引入鸿蒙SDK后，编译提示Cannot find module '@nimsdk/nim'。

## 排查过程

1. 检查引入方式 → 正确
2. 检查依赖安装 → 未执行ohpm install

## 问题原因

引入SDK后需要执行ohpm install安装依赖

## 解决方案

执行ohpm install命令安装模块依赖

## 其他触发场景

（合并时在此处追加）
