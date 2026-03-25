---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户头像
platform: 通用
title: 自定义头像URL被添加缩略参数
root_cause: SDK内部会根据缩略规则自动生成缩略地址，但客户自己的图片服务器不支持该规则
solution: 使用avatarUrl原图地址，不使用缩略图地址。或判断地址域名区分云信图片和客户图片。
customers: ["北京宝宝树"]
source: chat_history
tags: ["头像", "缩略图", "imageView", "avatarUrl"]
created: 2025-05-13
updated: 2025-03-20
---

## 问题：通用 自定义头像URL被添加缩略参数

## 问题详情

**现象**：
用户没有设置头像使用默认头像时，头像URL被自动添加了imageView&thumbnail=225z225参数，导致图片无法正常显示。

## 排查过程

**关键发现**：SDK内部会根据缩略规则自动生成缩略地址，但客户自己的图片服务器不支持该规则

## 问题原因

SDK内部会根据缩略规则自动生成缩略地址，但客户自己的图片服务器不支持该规则

## 解决方案

使用avatarUrl原图地址，不使用缩略图地址。或判断地址域名区分云信图片和客户图片。
