---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送服务
platform: Android
title: 华为推送证书配置和gradle编译问题
root_cause: agconnect插件配置位置错误，华为SDK版本需与IM版本兼容
solution: 1. 华为推送SDK需使用6.9.0.300版本与IM 9.7.0兼容
2. agconnect插件配置在app模块的build.gradle中，而非项目根目录
3. 证书名称自定义，保证SDK初始化时传的证书名和后台配置一致，不要用中文
customers: ["海南火焱科技有限公司"]
source: chat_history
tags: ["推送", "华为", "gradle", "agconnect", "Android"]
created: 2025-02-18
updated: 2026-03-20
---

## 问题：Android 华为推送证书配置和gradle编译问题

## 问题详情

**现象**：
客户反馈华为推送配置时gradle编译报错，agconnect插件添加失败。

## 排查过程

1. 确认IM SDK版本为9.7.0
2. 指导推送版本需与IM版本兼容，华为SDK需用6.9.0.300版本
3. 发现agconnect插件配置位置错误
4. 指导正确配置位置在app文件夹下的build.gradle而非项目根目录

## 问题原因

agconnect插件配置位置错误，华为SDK版本需与IM版本兼容

## 解决方案

1. 华为推送SDK需使用6.9.0.300版本与IM 9.7.0兼容
2. agconnect插件配置在app模块的build.gradle中，而非项目根目录
3. 证书名称自定义，保证SDK初始化时传的证书名和后台配置一致，不要用中文

## 其他触发场景

