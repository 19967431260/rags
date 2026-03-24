---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: iOS集成
platform: iOS
title: iOS SDK Bitcode导致AppStore审核失败
root_cause: 云信SDK包含bitcode，Xcode 14后AppStore不再接受含bitcode的二进制文件
solution: 参考文档去除bitcode：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ['临沂久讯网络科技有限公司']
source: chat_history
tags: ['iOS', 'Bitcode', 'AppStore', '审核', 'YXAlog_iOS']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS iOS SDK Bitcode导致AppStore审核失败

## 问题详情

**现象**：
iOS提交AppStore审核时遇到错误：YXAlog_iOS.framework包含bitcode，导致Invalid Executable错误。

## 排查过程



## 问题原因

云信SDK包含bitcode，Xcode 14后AppStore不再接受含bitcode的二进制文件

## 解决方案

参考文档去除bitcode：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加）
