---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 屏幕共享
platform: Uniapp
title: Uniapp打包iOS失败-App Groups权限问题
root_cause: RTC插件默认包含屏幕共享配置，需要App Groups权限，但客户不需要此功能
solution: 1. 如不需要屏幕共享功能，删除screenShareConfig.json文件
2. 删除manifest.json中的屏幕共享相关配置
3. 如需屏幕共享功能，参考文档开通App Groups权限：https://doc.yunxin.163.com/nertc/guide/TI5MjQzNjY?platform=uniapp
customers: ['重庆简房科技']
source: chat_history
tags: ['Uniapp', '打包失败', 'App Groups', '屏幕共享', 'iOS']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：Uniapp打包iOS失败-App Groups权限问题

## 问题详情

**现象**：
添加RTC插件后iOS打包失败，错误提示iOS账号没有App Groups权限。

## 排查过程

1. 检查错误日志发现缺少App Groups权限
2. 确认客户只需要音视频通话功能，不需要录屏
3. 检查插件配置发现包含屏幕共享配置

## 问题原因

RTC插件默认包含屏幕共享配置，需要App Groups权限，但客户不需要此功能

## 解决方案

1. 如不需要屏幕共享功能，删除screenShareConfig.json文件
2. 删除manifest.json中的屏幕共享相关配置
3. 如需屏幕共享功能，参考文档开通App Groups权限：https://doc.yunxin.163.com/nertc/guide/TI5MjQzNjY?platform=uniapp

## 其他触发场景

（合并时在此处追加）
