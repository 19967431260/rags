---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送服务
platform: Android
title: 华为推送token未上报问题
root_cause: 客户端推送SDK生成token有问题，或证书配置不正确
solution: 使用官方demo加上自己的华为证书配置测试，如能收到则是项目代码问题。检查初始化配置华为推送证书和华为相关配置，确保证书名与后台配置一致。
customers: ["海南火焱科技有限公司"]
source: chat_history
tags: ["推送", "华为", "token", "上报", "Android"]
created: 2025-02-18
updated: 2026-03-20
---

## 问题：Android 华为推送token未上报问题

## 问题详情

**现象**：
客户反馈华为推送token没有上报，后台收不到推送，但小米可以。

## 排查过程

1. 检查后台发现华为token没有上报
2. 确认推送token是推送SDK生成，云信SDK登录时自动上传
3. 没有上传一般是客户端推送SDK生成token有问题
4. 提供demo测试，demo可以收到推送

## 问题原因

客户端推送SDK生成token有问题，或证书配置不正确

## 解决方案

使用官方demo加上自己的华为证书配置测试，如能收到则是项目代码问题。检查初始化配置华为推送证书和华为相关配置，确保证书名与后台配置一致。

## 其他触发场景
- [Android] 华为推送token未上报问题，来源：['海南火焱科技有限公司']，2026-03-20

