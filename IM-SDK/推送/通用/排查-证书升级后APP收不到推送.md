---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: 通用
title: 证书升级后APP收不到推送
root_cause: iOS使用了错误的证书名，Android未传vivoCertificateName
solution: iOS检查初始化option.apnsCername设置，使用正确的证书名。Android需要传入vivoCertificateName。
customers: ["长沙校管家教育科技有限公司"]
source: chat_history
tags: ["IM", "推送", "证书", "iOS", "Android", "vivo"]
created: 2025-05-29
updated: 2025-03-20
---

## 问题：通用 证书升级后APP收不到推送

## 问题详情

**现象**：
证书升级后Android和iOS都收不到推送。

## 排查过程

**关键发现**：iOS使用了错误的证书名，Android未传vivoCertificateName

## 问题原因

iOS使用了错误的证书名，Android未传vivoCertificateName

## 解决方案

iOS检查初始化option.apnsCername设置，使用正确的证书名。Android需要传入vivoCertificateName。
