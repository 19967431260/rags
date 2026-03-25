---
track_type: 排查类
sub_type: SSL证书
product: IM-SDK
feature: SSL证书
platform: 服务端
title: curl请求返回SSL证书错误
root_cause: 网易云信于2025年4月25日进行*.netease.im证书升级，需要完成SSL证书根证书系统兼容性适配
solution: 网易云信于2025年4月25日进行*.netease.im证书升级，需要完成从DigiCert Global Root CA到DigiCert Global Root G2的SSL证书根证书系统兼容性适配。参考文档：https://doc.yunxin.163.com/messaging2/concept/zkyMzY2MDE?platform=client
customers: ["北京蔓云科技有限公司"]
source: chat_history
tags: ["SSL", "证书", "G2", "curl", "DigiCert"]
created: 2025-05-28
updated: 2025-03-23
---

## 问题：服务端 curl请求返回SSL证书错误

## 问题详情

**现象**：
调用API时curl返回SSL证书问题，已下载G2证书但仍返回false

**环境信息**：
- 平台：服务端

## 排查过程

**关键发现**：SSL证书升级导致兼容性问题

## 问题原因

网易云信于2025年4月25日进行*.netease.im证书升级，需要完成SSL证书根证书系统兼容性适配

## 解决方案

网易云信于2025年4月25日进行*.netease.im证书升级，需要完成从DigiCert Global Root CA到DigiCert Global Root G2的SSL证书根证书系统兼容性适配。参考文档：https://doc.yunxin.163.com/messaging2/concept/zkyMzY2MDE?platform=client
