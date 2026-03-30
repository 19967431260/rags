---
track_type: 排查类
sub_type: Demo问题
product: IM-UIKit
feature: 初始化配置
platform: Web
title: Vue3中renderImDisconnected配置无效
root_cause: 文档中属性名大小写错误，应为renderImDisconnected而非renderIm disconnected
solution: 注意属性名大小写：renderImDisconnected。Vue3中需要在provider内配置。
customers: ["元拓科技（大连）有限公司"]
source: chat_history
tags: ["Vue3","renderImDisconnected","断连渲染","类型错误"]
created: 2025-06-05
updated: 2025-06-05
---

## 问题：Web Vue3中renderImDisconnected配置无效

## 问题详情

**现象**：
客户在Vue3项目中配置renderImDisconnected断连渲染函数，发现类型报错且配置无效。

## 排查过程

1. 确认配置位置是否在provider内 → 检查配置位置
2. 检查属性名大小写 → 检查属性名
3. 发现文档中属性名大小写与实际代码不一致 → 确定问题根因

**关键发现**：文档中属性名大小写错误，应为renderImDisconnected而非renderIm disconnected

## 问题原因

文档中属性名大小写错误，应为renderImDisconnected而非renderIm disconnected

## 解决方案

注意属性名大小写：renderImDisconnected。Vue3中需要在provider内配置。

## 其他触发场景

