---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录
platform: iOS
title: M1芯片Mac打包iOS应用YXLogin.framework报错
root_cause: YXLogin.framework（统一登录库）在M1芯片Mac上打包时bitcode不完整。
solution: 解决方案：1）如不需要统一登录功能，可直接移除YXLogin.framework；2）如需使用，联系技术支持获取适配M1芯片的版本。
customers: ["济南时代"]
source: chat_history
tags: ["M1芯片", "bitcode", "YXLogin", "iOS打包", "App Store"]
created: 2025-05-08
updated: 2025-03-20
---

## 问题：iOS M1芯片Mac打包iOS应用YXLogin.framework报错

## 问题详情

**现象**：
使用M1芯片的Mac打包iOS应用上传App Store时，YXLogin.framework报错：Invalid Bundle Executable，contains incomplete bitcode。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程

1. 客户反馈M1芯片打包报错 → 技术支持建议检查bitcode
2. 客户按文档检查bitcode正常 → 建议升级YXLogin版本
3. 客户使用1.1.0版本 → 建议升级到1.0.9或去掉该库

## 问题原因

YXLogin.framework（统一登录库）在M1芯片Mac上打包时bitcode不完整。

## 解决方案

解决方案：1）如不需要统一登录功能，可直接移除YXLogin.framework；2）如需使用，联系技术支持获取适配M1芯片的版本。

## 其他触发场景

