---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: Framework打包
platform: iOS
title: NERtcnn.framework包含bitcode导致打包失败
root_cause: NERtcnn.framework包含bitcode，Xcode新版本不支持
solution: 参考文档处理，需要单独处理每个framework路径移除bitcode，目前只能单独处理
customers: ['杭州云汽配配科技有限公司']
source: chat_history
tags: ['bitcode', 'NERtcnn', '打包失败', 'iOS', 'Framework']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：iOS NERtcnn.framework包含bitcode导致打包失败

## 问题详情

**现象**：
打包上传App Store报错：Invalid Executable. The executable 'Runner.app/Frameworks/NERtcnn.framework/NERtcnn' contains bitcode

## 排查过程



## 问题原因

NERtcnn.framework包含bitcode，Xcode新版本不支持

## 解决方案

参考文档处理，需要单独处理每个framework路径移除bitcode，目前只能单独处理

## 其他触发场景

（合并时在此处追加）
