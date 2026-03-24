---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 离线推送
platform: Android
title: 荣耀推送token上传失败certificate fingerprint error
root_cause: 荣耀推送证书指纹配置错误
solution: 参考荣耀官方文档检查证书指纹配置：https://blog.csdn.net/HUAWEI_HMSCore/article/details/136656758
customers: ['广西珍心传媒']
source: chat_history
tags: ['荣耀推送', 'certificate fingerprint', '6003', 'token上传']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Android 荣耀推送token上传失败certificate fingerprint error

## 问题详情

**现象**：
客户配置荣耀推送后，token上传失败，报错6003: certificate fingerprint error。

## 排查过程

1. 客户反馈荣耀推送token上传失败
2. 报错信息：query token with exception 6003: certificate fingerprint error
3. 技术支持确认这是荣耀那边的错误码
4. 提供了荣耀官方错误码文档链接

## 问题原因

荣耀推送证书指纹配置错误

## 解决方案

参考荣耀官方文档检查证书指纹配置：https://blog.csdn.net/HUAWEI_HMSCore/article/details/136656758

## 其他触发场景

（合并时在此处追加）
