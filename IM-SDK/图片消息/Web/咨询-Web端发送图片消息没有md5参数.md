---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-SDK
feature: 图片消息
platform: Web
title: Web端发送图片消息没有md5参数
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# Web端发送图片消息没有md5参数

## 问题描述

Web端发送图片消息时，三方回调中没有md5参数，而Android端有

## 问题背景

- 对比Web端和Android端发送图片的回调数据，Web端attach中没有md5字段

## 解答

Web端发送图片时可能无法获取md5值，属于正常现象。如需使用md5，可以在业务层自己计算然后塞在扩展字段里。

## 标签

- Web
- 图片消息
- md5
- 三方回调

## 客户

- FVIP云信-时间在线-gj

## 会话日期

2025-02-07
