---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK升级
platform: 安卓
title: IM SDK从8.9升级到10.7编译出错
root_cause: 8.9到10.x系列API接口全部重构，10.x使用V2NIMMessage替代IMMessage
solution: 8.9不建议直接升级到10.x系列，可以先升级到9.x版本。如需使用10.x，需要继承新的V2NIMMessage并同步升级API接口。如无10.x新功能需求，建议继续沿用9.x版本。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# IM SDK从8.9升级到10.7编译出错

## 问题描述

客户将IM SDK从8.9直接升级到10.7后编译报错，MessageWrapper类实现IMMessage接口时提示未覆盖抽象方法setErrorCodeOfMessageStatus

## 问题背景

- 检查SDK版本兼容性，建议不要直接跨大版本升级

## 根因分析

8.9到10.x系列API接口全部重构，10.x使用V2NIMMessage替代IMMessage

## 解决方案

8.9不建议直接升级到10.x系列，可以先升级到9.x版本。如需使用10.x，需要继承新的V2NIMMessage并同步升级API接口。如无10.x新功能需求，建议继续沿用9.x版本。

## 标签

- SDK升级
- 版本兼容
- V9
- V10
- 编译错误
- IMMessage

## 客户

- FVIP云信-深圳富旅奇缘

## 会话日期

2025-02-07
