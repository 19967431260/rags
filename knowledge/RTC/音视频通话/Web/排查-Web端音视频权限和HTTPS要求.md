---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: Web
title: Web端音视频权限和HTTPS要求
root_cause: WebRTC要求HTTPS环境才能访问媒体设备，HTTP部署无法获取摄像头和麦克风权限
solution: 必须使用HTTPS部署WebRTC应用，浏览器才会允许访问媒体设备
customers: ['河北圣诺联合科技有限公司']
source: chat_history
tags: ['WebRTC', 'HTTPS', '权限', '媒体设备', 'HTTP']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：Web Web端音视频权限和HTTPS要求

## 问题详情

**现象**：
部署到服务器后无法访问媒体设备，本地可以，提示权限错误。

## 排查过程

1. 确认浏览器权限已开启
2. demo测试可以访问设备
3. 发现部署地址是http://183.196.101.243:8181/
4. 判断是HTTP导致的问题

## 问题原因

WebRTC要求HTTPS环境才能访问媒体设备，HTTP部署无法获取摄像头和麦克风权限

## 解决方案

必须使用HTTPS部署WebRTC应用，浏览器才会允许访问媒体设备

## 其他触发场景

（合并时在此处追加）
