---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 文件上传下载
platform: Web
title: Web端私有化图片消息域名配置错误
root_cause: Web端私有化初始化参数配置不完整，缺少chunkUploadHost、uploadReplaceFormat、downloadHost、downloadReplaceFormat等配置
solution: 按照标准格式配置Web端私有化参数：lbsUrls、linkUrl、chunkUploadHost、uploadReplaceFormat（格式：https://域名/yunxin/{object}）、downloadHost、downloadReplaceFormat
customers: ["信雅达（晋商银行）"]
source: chat_history
tags: ["Web","私有化配置","图片消息","文件上传","域名配置"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Web Web端私有化图片消息域名配置错误

## 问题详情

**现象**：
Web端发送图片消息后，坐席端收到的图片消息无法显示，url域名格式不正确。

## 排查过程

1. 检查消息内容 → url格式为rvb.scrmtest.top/{bucket}/xxx
2. 检查初始化配置 → 发现私有化参数配置不完整

**关键发现**：Web端私有化需要配置完整的上传下载参数

## 问题原因

Web端私有化初始化参数配置不完整，缺少chunkUploadHost、uploadReplaceFormat、downloadHost、downloadReplaceFormat等配置

## 解决方案

按照标准格式配置Web端私有化参数：lbsUrls、linkUrl、chunkUploadHost、uploadReplaceFormat（格式：https://域名/yunxin/{object}）、downloadHost、downloadReplaceFormat。

## 其他触发场景

（暂无）
