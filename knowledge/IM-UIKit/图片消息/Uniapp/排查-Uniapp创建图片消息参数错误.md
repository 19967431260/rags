---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 图片消息
platform: Uniapp
title: Uniapp创建图片消息参数错误
root_cause: createImageMessage接口接受的是args参数（文件路径），而非imageObj对象，客户看错文档参数类型
solution: createImageMessage直接传入图片文件路径参数，如：createImageMessage(res.tempFilePaths[0])
customers: ['北京圆心医疗']
source: chat_history
tags: ['createImageMessage', '图片消息', 'Uniapp', '参数错误', 'V2NIM']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Uniapp Uniapp创建图片消息参数错误

## 问题详情

**现象**：
客户使用V2NIMMessageCreator.createImageMessage创建图片消息时报错，不确定参数如何传递。

## 排查过程

1. 检查错误信息 → 发现路径不存在
2. 检查API用法 → 客户误以为需要传imageObj对象
3. 关键发现：createImageMessage接受的是args参数而非object

## 问题原因

createImageMessage接口接受的是args参数（文件路径），而非imageObj对象，客户看错文档参数类型

## 解决方案

createImageMessage直接传入图片文件路径参数，如：createImageMessage(res.tempFilePaths[0])

## 其他触发场景

（合并时在此处追加）
