---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: HTTPS证书
platform: 服务端
title: Java 1.7访问新域名SSL证书握手失败
root_cause: Java 1.7证书库不包含DigiCert Global Root G2根证书
solution: 方案1：升级到Java 1.8；方案2：手动导入DigiCert Global Root G2根证书到证书库
customers: ["北京助梦工场"]
source: chat_history
tags: ["SSL", "证书", "Java 1.7", "握手失败", "域名迁移"]
created: 2025-05-13
updated: 2025-03-20
---

## 问题：服务端 Java 1.7访问新域名SSL证书握手失败

## 问题详情

**现象**：
使用Java 1.7访问新域名api-weimaiquan.yunxinapi.com时出现SSLHandshakeException，无法找到有效的证书路径。

## 排查过程

**关键发现**：Java 1.7证书库不包含DigiCert Global Root G2根证书

## 问题原因

Java 1.7证书库不包含DigiCert Global Root G2根证书

## 解决方案

方案1：升级到Java 1.8；方案2：手动导入DigiCert Global Root G2根证书到证书库
