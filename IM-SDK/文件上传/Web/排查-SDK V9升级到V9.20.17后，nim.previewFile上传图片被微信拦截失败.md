---
track_type: 排查类
sub_type: 功能异常
product: IM-SDK
feature: 文件上传
platform: Web
title: SDK V9升级到V9.20.17后，nim.previewFile上传图片被微信拦截失败
root_cause: 小程序域名白名单配置缺失
solution: 在小程序后台配置新增的上传域名白名单
customers: ["FVIP-云信-上海抱朴"]
source: chat_history
tags: ["小程序", "IM V9", "previewFile", "上传失败", "域名白名单"]
created: 2025-12-02
updated: 2026-03-23
---

## 问题：微信小程序IM SDK V9升级到V9.20.17后，nim.previewFile上传图片被微信拦截失败

## 问题详情

**现象**：
微信小程序IM SDK从V9升级到V9.20.17版本后，调用`nim.previewFile`上传图片时被微信拦截，上传失败。

**环境信息**：
- SDK 版本：V9.20.17
- 平台：微信小程序

## 排查过程

1. 确认SDK版本升级后出现的问题 → 判断为版本升级导致的配置变更
2. 检查小程序域名白名单配置 → 发现缺少新增的上传域名

**关键发现**：V9.20.17版本新增了上传域名，需要在小程序后台配置白名单

## 问题原因

V9.20.17版本新增了上传域名，但小程序后台未配置对应的域名白名单，导致上传请求被微信拦截。

## 解决方案

在小程序后台配置新增的上传域名白名单。

参考文档：https://doc.yunxin.163.com/messaging/concept/DM3MTMxOTE?platform=client

## 其他触发场景

