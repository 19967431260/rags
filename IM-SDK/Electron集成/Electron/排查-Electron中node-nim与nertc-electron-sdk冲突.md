---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Electron集成
platform: Electron
title: Electron中node-nim与nertc-electron-sdk冲突
root_cause: node-nim和nertc-electron-sdk的webpack loader配置冲突，路径解析不一致
solution: 1. 安装node-nim@beta最新版 2. 恢复webpack.config.preload.js原始配置 3. 在window.ts中添加node-nim路径到PATH环境变量
customers: ["深圳联友"]
source: chat_history
tags: ["node-nim", "nertc-electron-sdk", "webpack", "Electron", "loader"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Electron中node-nim与nertc-electron-sdk冲突

## 问题详情

**现象**：
在Electron项目中同时引入node-nim和nertc-electron-sdk时出现加载冲突，webpack配置复杂

**环境信息**：
- 平台：Electron

## 排查过程

1. 检查webpack配置 → 发现node加载器配置问题
2. 分析路径解析 → 不同平台路径处理不一致
3. 优化require脚本 → 统一加载路径到同一目录
4. 调整环境变量 → 在window.ts中添加PATH配置

## 根因分析

node-nim和nertc-electron-sdk的webpack loader配置冲突，路径解析不一致

## 解决方案

1. 安装node-nim@beta最新版 2. 恢复webpack.config.preload.js原始配置 3. 在window.ts中添加node-nim路径到PATH环境变量

## 其他触发场景

（无）
