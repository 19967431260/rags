---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 屏幕共享
platform: iOS
title: 网易会议Flutter iOS屏幕共享PBXFileSystemSynchronizedRootGroup不兼容
root_cause: 与本地Xcode和CocoaPods版本兼容性有关，需要检查项目配置。
solution: 参考CSDN文章处理Xcode 16与CocoaPods兼容性问题：https://blog.csdn.net/abcliuliu120/article/details/142732750。如仍有问题，检查本地项目环境配置。
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['网易会议', 'Flutter', 'iOS', '屏幕共享', 'Xcode 16', 'CocoaPods', 'PBXFileSystemSynchronizedRootGroup']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：iOS 网易会议Flutter iOS屏幕共享PBXFileSystemSynchronizedRootGroup不兼容

## 问题详情

**现象**：
客户反馈配置屏幕共享后出现PBXFileSystemSynchronizedRootGroup不兼容问题，Xcode 16 CocoaPods 1.15.2最新版本。

## 排查过程

1. 确认flutter会议源码地址 → 提供GitHub地址
2. 分析报错 → 与本地项目环境配置有关
3. 建议排查 → 按照网上逻辑处理，检查本地项目配置

## 问题原因

与本地Xcode和CocoaPods版本兼容性有关，需要检查项目配置。

## 解决方案

参考CSDN文章处理Xcode 16与CocoaPods兼容性问题：https://blog.csdn.net/abcliuliu120/article/details/142732750。如仍有问题，检查本地项目环境配置。

## 其他触发场景

（合并时在此处追加）
