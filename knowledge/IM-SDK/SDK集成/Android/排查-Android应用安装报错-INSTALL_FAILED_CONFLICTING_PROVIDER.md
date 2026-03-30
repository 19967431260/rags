---
track_type: 排查类
sub_type: 集成问题
product: IM-SDK
feature: Android集成
platform: Android
title: Android应用安装报错：INSTALL_FAILED_CONFLICTING_PROVIDER 内容提供者冲突
root_cause: provider的authorities配置中使用了默认的demo包名，与其他使用云信SDK的应用冲突
solution: 将AndroidManifest.xml中云信provider的authorities从默认的demo包名(com.netease.nim.demo)修改为应用自己的包名。具体需要修改的provider包括：1. com.netease.nimlib.ipc.NIMContentProvider - 将authorities改为${applicationId}.ipc.provider；2. com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider - 将authorities改为${applicationId}.ipc.provider.preference。确保所有authorities都使用应用自身的包名，避免与其他应用冲突。
customers: ["杭州搬多多科技有限公司"]
source: chat_history
tags: ["Android", "安装冲突", "Provider", "ContentProvider", "INSTALL_FAILED_CONFLICTING_PROVIDER", "包名冲突"]
created: 2025-05-19
updated: 2025-03-23
---

## 问题：Android Android应用安装报错：INSTALL_FAILED_CONFLICTING_PROVIDER 内容提供者冲突

## 问题详情

**现象**：
在Android设备上安装应用时，报错'The application could not be installed: INSTALL_FAILED_CONFLICTING_PROVIDER'，提示内容提供者冲突，与一款叫芝麻体育的app冲突。问题原因是provider的authorities配置中使用了默认的demo包名(com.netease.nim.demo.ipc.provider.preference)，与其他使用云信SDK的应用冲突。

**环境信息**：
- 平台：Android

## 排查过程

**关键发现**：provider的authorities配置使用了默认demo包名

## 问题原因

provider的authorities配置中使用了默认的demo包名，与其他使用云信SDK的应用冲突

## 解决方案

将AndroidManifest.xml中云信provider的authorities从默认的demo包名(com.netease.nim.demo)修改为应用自己的包名。具体需要修改的provider包括：
1. com.netease.nimlib.ipc.NIMContentProvider - 将authorities改为${applicationId}.ipc.provider
2. com.netease.nimlib.ipc.cp.provider.PreferenceContentProvider - 将authorities改为${applicationId}.ipc.provider.preference
确保所有authorities都使用应用自身的包名，避免与其他应用冲突。
