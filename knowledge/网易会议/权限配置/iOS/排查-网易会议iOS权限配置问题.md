---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 权限配置
platform: iOS
title: 网易会议iOS权限配置问题
root_cause: iOS工程权限配置不完整，需要在Xcode中配置相关权限，flutter源码工程需要拷贝podfile中的权限配置段。
solution: 在Xcode中配置iOS权限，参考文档：https://doc.yunxin.163.com/meeting/guide/zg0NTkxMjY?platform=iOS。如果是flutter源码工程，需要检查meetingapp下的ios podfile最后一段权限配置是否拷贝到工程。
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['网易会议', 'Flutter', 'iOS', '权限', 'Xcode', 'podfile']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：iOS 网易会议iOS权限配置问题

## 问题详情

**现象**：
客户反馈iOS端音视频、相册、拍照功能都用不了，咨询权限配置。

## 排查过程

1. 确认问题 → 音视频、相册、拍照功能不可用
2. 提供配置文档 → 参考官方文档配置Xcode权限
3. 进一步排查 → 发现是flutter源码权限问题
4. 建议检查 → 检查meetingapp下的ios podfile配置

## 问题原因

iOS工程权限配置不完整，需要在Xcode中配置相关权限，flutter源码工程需要拷贝podfile中的权限配置段。

## 解决方案

在Xcode中配置iOS权限，参考文档：https://doc.yunxin.163.com/meeting/guide/zg0NTkxMjY?platform=iOS。如果是flutter源码工程，需要检查meetingapp下的ios podfile最后一段权限配置是否拷贝到工程。

## 其他触发场景

（合并时在此处追加）
