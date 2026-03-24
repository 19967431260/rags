---
track_type: 排查类
sub_type: 测试问题
product: IM-UIKit
feature: UI组件
platform: Uniapp
title: Uniapp UIKit Demo运行报错403
root_cause: Uniapp UIKit Demo在内置浏览器中无法正常运行，需要使用外部浏览器
solution: 使用外部浏览器运行Demo，不要使用HBuilderX内置浏览器
customers: ['成都学海方舟教育咨询有限责任公司']
source: chat_history
tags: ['UIKit', 'Uniapp', 'Demo', '403', '浏览器兼容性']
created: 2025-01-03
updated: 2026-03-23
---

## 问题：Uniapp UIKit Demo运行报错403

## 问题详情

**现象**：
客户运行Uniapp UIKit Demo时出现403权限错误，页面无法正常进入。

## 排查过程

1. 客户提供报错截图 → 发现是客户端反垃圾和AI数字人功能报错
2. 确认appkey和account信息 → 登录正常
3. 建议保存控制台日志 → 客户尝试内置浏览器和外部浏览器
**关键发现**：内置浏览器无法运行，外部浏览器可以正常运行

## 问题原因

Uniapp UIKit Demo在内置浏览器中无法正常运行，需要使用外部浏览器

## 解决方案

使用外部浏览器运行Demo，不要使用HBuilderX内置浏览器

## 其他触发场景

（合并时在此处追加）
