---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 文件上传
platform: Web
title: Web端分片上传缺少chunkUploadUrl配置
root_cause: 私有化环境缺少chunkUploadUrl配置参数，导致分片上传无法正常工作
solution: 在初始化配置中添加chunkUploadUrl参数，指向分片上传地址。commonUpload保持默认false即可使用分片上传。
customers: ['翼信']
source: chat_history
tags: ['分片上传', 'chunkUploadUrl', '文件上传', '100M限制', 'Web端']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Web Web端分片上传缺少chunkUploadUrl配置

## 问题详情

**现象**：
客户从普通上传改为分片上传后报错，需要去掉100M文件大小限制。普通上传限制100MB，分片上传需要配置chunkUploadUrl参数。

## 排查过程

1. 客户反馈去掉100M限制后改为分片上传报错
2. 检查配置发现缺少chunkUploadUrl参数
3. 该参数控制分片上传的地址，之前未配置所以一直走普通上传
4. 配置chunkUploadUrl后问题解决

## 问题原因

私有化环境缺少chunkUploadUrl配置参数，导致分片上传无法正常工作

## 解决方案

在初始化配置中添加chunkUploadUrl参数，指向分片上传地址。commonUpload保持默认false即可使用分片上传。

## 其他触发场景

（合并时在此处追加）
