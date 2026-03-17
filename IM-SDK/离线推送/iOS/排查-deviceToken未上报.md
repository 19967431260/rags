---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS推送deviceToken未上报问题
root_cause: 客户使用了错误的推送配置API方法，导致推送token无法生成；同时管理后台推送证书名与客户端配置不一致
solution: 使用正确的API：nim.V2NIMSettingService.setOfflinePushConfig进行推送配置，确保管理后台的推送证书名与客户端配置的certificateName一致。参考文档：https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp
customers: ["重庆炽焰体育科技有限公司"]
source: chat_history
tags: ["iOS", "deviceToken", "推送配置", "证书名称", "setOfflinePushConfig"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：iOS iOS推送deviceToken未上报问题

## 问题详情

**现象**：
Uniapp iOS端集成推送后，退后台无法收到通知栏推送。日志显示推送token未生成，deviceToken未上报到服务端。

**环境信息**：
- 平台：Uniapp自定义基座
- 证书：iOS测试证书

## 排查过程

1. 检查日志 → 发现推送token未生成，deviceToken未上报
2. 检查推送插件集成 → 客户确认已集成官网下载的插件
3. 检查推送配置代码 → 发现客户使用了错误的API
4. 检查bundle ID和Push Notifications权限 → 确认一致且已开启
5. 检查推送证书配置 → 发现管理后台证书名(IOSPUSH)与客户端配置(NIM****_DEV)不一致

**关键发现**：客户使用了错误的推送配置方法，应使用nim.V2NIMSettingService.setOfflinePushConfig而非其他方法；推送证书名必须保持管理后台与客户端一致

## 问题原因

客户使用了错误的推送配置API方法，导致推送token无法生成；同时管理后台推送证书名与客户端配置不一致

## 解决方案

使用正确的API：nim.V2NIMSettingService.setOfflinePushConfig进行推送配置，确保管理后台的推送证书名与客户端配置的certificateName一致。参考文档：https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp

## 其他触发场景

