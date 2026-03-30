---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 分包
platform: Uniapp
title: IM UIKit Uniapp分包后报错
root_cause: 分包后部分依赖未正确引入导致
solution: 基于官方demo添加分包配置进行复现测试，对比排查依赖问题；官方demo地址：https://github.com/netease-kit/nim-uikit-uniapp/tree/main/im-uniapp-ui
customers: ["VIP云信-上海闲途科技有限公司"]
source: chat_history
tags: ["UIKit", "Uniapp", "分包", "小程序", "体积"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Uniapp IM UIKit Uniapp分包后报错

## 问题详情

**现象**：
使用IM UIKit后小程序包体积过大，进行Uniapp分包配置后运行报错

## 排查过程

1. 确认分包配置 → subPackages配置
2. 对比demo测试 → demo分包可正常运行
3. 分析差异 → 可能缺少依赖

## 问题原因

分包后部分依赖未正确引入导致

## 解决方案

基于官方demo添加分包配置进行复现测试，对比排查依赖问题；官方demo地址：https://github.com/netease-kit/nim-uikit-uniapp/tree/main/im-uniapp-ui

## 其他触发场景

