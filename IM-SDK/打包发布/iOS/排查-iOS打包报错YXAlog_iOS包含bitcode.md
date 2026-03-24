---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 打包发布
platform: iOS
title: iOS打包报错YXAlog_iOS包含bitcode
root_cause: Xcode误报bitcode问题，SDK实际未使用bitcode。
solution: 使用xcrun bitcode_strip命令去除bitcode标记：cd到framework目录，执行xcrun bitcode_strip -r YXAlog_iOS.framework/YXAlog_iOS -o YXAlog_iOS.framework/YXAlog_iOS。参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ['杭州泰阿网络']
source: chat_history
tags: ['iOS', 'bitcode', '打包', 'YXAlog', '错误']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：iOS iOS打包报错YXAlog_iOS包含bitcode

## 问题详情

**现象**：
客户打包时遇到错误：Invalid Executable. The executable 'app.app/Frameworks/YXAlog_iOS.framework/YXAlog_iOS' contains bitcode.

## 排查过程



## 问题原因

Xcode误报bitcode问题，SDK实际未使用bitcode。

## 解决方案

使用xcrun bitcode_strip命令去除bitcode标记：cd到framework目录，执行xcrun bitcode_strip -r YXAlog_iOS.framework/YXAlog_iOS -o YXAlog_iOS.framework/YXAlog_iOS。参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加）
