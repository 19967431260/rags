---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 图片消息
platform: Android
title: Android端图片消息发送失败
root_cause: 日志上传和发文件类消息都是先走CDN上传，可能是用户当前网络访问CDN服务出现问题
solution: 1. 让用户切换到WI-FI网络下再尝试
2. 运维侧检查当地CDN节点解析情况
3. 如果问题持续，需要提供用户IP和云信账号拉取SDK日志进一步分析
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# Android端图片消息发送失败

## 问题描述

用户反馈图片消息发送失败，显示感叹号，文字消息正常

## 问题背景

- IM登录正常，文字消息发送成功
- 仅图片/文件类型消息失败
- 用户只有移动数据网络

## 根因分析

日志上传和发文件类消息都是先走CDN上传，可能是用户当前网络访问CDN服务出现问题

## 解决方案

1. 让用户切换到WI-FI网络下再尝试
2. 运维侧检查当地CDN节点解析情况
3. 如果问题持续，需要提供用户IP和云信账号拉取SDK日志进一步分析

## 标签

- Android
- 图片消息
- CDN
- 网络问题
- 发送失败

## 客户

- FVIP云信-南京麦豆健康

## 会话日期

2025-02-18
