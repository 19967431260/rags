---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 账号登录
platform: Uniapp
title: IM V10 Uniapp SDK账号体系与登录对接方案
root_cause: 
solution: 业务层鉴权完成后，将云信的accid和token返回给客户端，客户端再调用IM SDK登录。支持静态token和动态token混合使用。
customers: ['辽宁轻舟潮娱科技有限公司']
source: chat_history
tags: ['V10', 'Uniapp', '账号对接', '登录流程', 'sa-token']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：IM V10 Uniapp SDK账号体系与登录对接方案

## 问题详情

**现象**：
客户已有业务层账号体系（sa-token），需要与云信IM账号体系对接，实现业务登录后自动登录IM。

## 排查过程



## 问题原因



## 解决方案

业务层鉴权完成后，将云信的accid和token返回给客户端，客户端再调用IM SDK登录。支持静态token和动态token混合使用。

## 其他触发场景

（合并时在此处追加）
