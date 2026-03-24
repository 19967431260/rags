---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: iOS集成
platform: iOS
title: iOS打包上传AppStore提示SDK包含bitcode
root_cause: SDK包含bitcode，AppStore要求移除
solution: 按照文档移除NIMNOS的bitcode，参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ['可思达地信息科技']
source: chat_history
tags: ['iOS', 'bitcode', 'AppStore', '打包', 'NIMSDK_LITE']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：iOS iOS打包上传AppStore提示SDK包含bitcode

## 问题详情

**现象**：
客户使用NIMSDK_LITE 9.12.1版本，iOS打包上传AppStore时提示云信SDK包含bitcode问题。

## 排查过程

1. 客户反馈iOS打包上传AppStore提示SDK问题
2. 确认使用的是NIMSDK_LITE 9.12.1
3. 提供bitcode移除方案

## 问题原因

SDK包含bitcode，AppStore要求移除

## 解决方案

按照文档移除NIMNOS的bitcode，参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加）
