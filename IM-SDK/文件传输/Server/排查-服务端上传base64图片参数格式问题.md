---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 文件传输
platform: Server
title: 服务端上传base64图片参数格式问题
root_cause: 上传base64图片时，需要去掉data:image/png;base64,前缀，从iVBO开始保留，同时type参数传image/png
solution: 去掉base64的data:image/png;base64,前缀，只保留从iVBO开始的纯base64内容，type参数传image/png
customers: ['杭州量子世界']
source: chat_history
tags: ['base64', '图片上传', 'upload', '服务端API']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Server 服务端上传base64图片参数格式问题

## 问题详情

**现象**：
客户使用服务端API上传base64编码的图片，返回的URL无法正常访问，图片显示损坏。

## 排查过程

1. 检查base64内容 → 正常
2. 检查URL → 无法打开
3. 对比APP端正常URL → 发现差异
4. 验证传参格式 → 发现base64前缀问题

## 问题原因

上传base64图片时，需要去掉data:image/png;base64,前缀，从iVBO开始保留，同时type参数传image/png

## 解决方案

去掉base64的data:image/png;base64,前缀，只保留从iVBO开始的纯base64内容，type参数传image/png

## 其他触发场景

（合并时在此处追加）
