---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Windows
platform: Windows
title: Windows x64版本图片发送卡0%
root_cause: SDK根目录的cacert.pem文件未拷贝到bin文件夹下，导致HTTPS上传失败
solution: 将SDK根目录的cacert.pem文件放到bin文件夹下再上传
customers: ['VIP云信-广州敬汕贸易有限公司']
source: chat_history
tags: ['Windows', 'x64', '图片发送', 'cacert.pem', '上传']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Windows Windows x64版本图片发送卡0%

## 问题详情

**现象**：
Windows x64版本图片发送不出去，一直卡在0%

## 排查过程

1. 查看日志 → 发现上传问题
2. 检查证书文件 → 发现缺少cacert.pem

## 问题原因

SDK根目录的cacert.pem文件未拷贝到bin文件夹下，导致HTTPS上传失败

## 解决方案

将SDK根目录的cacert.pem文件放到bin文件夹下再上传

## 其他触发场景

（合并时在此处追加）
