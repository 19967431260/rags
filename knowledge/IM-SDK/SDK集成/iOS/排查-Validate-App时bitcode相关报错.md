---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK集成
platform: iOS
title: "Validate App时bitcode相关报错"
root_cause: "集成了七鱼SDK（QY_NIM_iOS_SDK），七鱼在云信SDK上包了一层，版本控制复杂，导致bitcode问题。"
solution: "参考文档处理bitcode：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client。这是万能的处理方法，适用于集成了多个SDK的情况。"
customers: ["ISHOPSHOPS"]
source: chat_history
tags: ["bitcode", "NIMKit", "七鱼", "QY_NIM_iOS_SDK", "Validate App"]
created: 2026-01-22
updated: 2026-03-15
---

## 问题：iOS Validate App时bitcode相关报错

## 问题详情

**现象**：
使用NIMKit/Lite_Free和QY_NIM_iOS_SDK时，Validate App报bitcode相关错误。

## 排查过程



## 问题原因

集成了七鱼SDK（QY_NIM_iOS_SDK），七鱼在云信SDK上包了一层，版本控制复杂，导致bitcode问题。

## 解决方案

参考文档处理bitcode：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client。这是万能的处理方法，适用于集成了多个SDK的情况。

## 其他触发场景

（暂无）
