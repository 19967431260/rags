---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: SDK集成
platform: Electron
title: Electron集成RTC SDK运行报错配置方案
root_cause: 
solution: 详见正文。
customers: ["科蓝"]
source: chat_history
tags: ["Electron", "webpack", "contextIsolation", "crypto-js", "nertc-electron-sdk"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题描述

Electron项目集成nertc-electron-sdk后运行报错，参考demo配置rules后仍有报错，使用webpack5。

## 排查过程

1. 客户反馈Electron集成后运行报错 → 要求提供复现工程
2. 客户demo npm install报错 → 建议删除node_modules重装
3. 客户环境满足要求但运行报错 → 建议设置contextIsolation: false
4. 设置后其他包报错 → 建议修改webpack配置路径
5. 引入其他组件报错 → 建议更换md5库为crypto-js

## 根因分析

Electron上下文隔离和webpack配置兼容性问题

## 解决方案

1. webPreferences设置contextIsolation: false
2. 修改webpack配置路径
3. 如有md5库兼容问题可更换为crypto-js
4. 推荐使用electron-vite脚手架减少兼容性问题
