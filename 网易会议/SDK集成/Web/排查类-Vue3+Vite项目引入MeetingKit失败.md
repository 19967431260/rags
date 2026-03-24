---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: SDK集成
platform: Web
title: Vue3+Vite项目引入MeetingKit失败
root_cause: Vue3+Vite框架对UMD模块的兼容性问题
solution: 参考提供的demo项目，调整kit引入顺序在main.ts之前，使用正确的引入方式
customers: ['四川众泰云鼎科技有限公司']
source: chat_history
tags: ['网易会议', 'MeetingKit', 'Vue3', 'Vite', '模块化引入', 'Web']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Vue3+Vite项目引入MeetingKit失败

## 问题详情

**现象**：
客户在Vue3+Vite项目中通过模块化方式引入NEMeetingKit失败，报错require is not defined或NEMeetingKit is not defined。

## 排查过程

1. 客户尝试import { default } from方式引入失败
2. 建议直接使用import NEMeetingKit from方式
3. 客户升级到4.11.0版本仍报错
4. 确认是vite框架问题，提供demo参考
5. 建议调整引入顺序，在main.ts之前引入
6. 最终提供完整demo项目

## 问题原因

Vue3+Vite框架对UMD模块的兼容性问题

## 解决方案

参考提供的demo项目，调整kit引入顺序在main.ts之前，使用正确的引入方式

## 其他触发场景

（合并时在此处追加）
