---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: OPPO离线推送收不到推送
root_cause: 代码中配置的appkey与云信控制台后台配置的appkey不一致，导致推送证书无法匹配
solution: 检查并确保代码中配置的appkey与云信控制台后台配置的appkey完全一致。
customers: ['广西珍心传媒']
source: chat_history
tags: ['OPPO', '离线推送', 'appkey', '推送证书', 'mix push']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Android OPPO离线推送收不到推送

## 问题详情

**现象**：
客户反馈OPPO手机私信离线推送收不到，mix push init config显示为null。

## 排查过程

1. 客户反馈mix push init config = null，怀疑推送初始化未成功
2. 技术支持要求提供完整SDK日志
3. 查看日志发现token已生成：OPPO_CN_2465bd7ee7d81ba45d1845d4c8b3a515
4. 技术支持发现客户配置的appkey与实际后台配置不匹配
5. 客户确认代码中配置的appkey是307e75388b48fa2d24a2a823533effce
6. 后台实际配置的是0681614ec7d31f1614ab6751c9970161
7. 根因确定：appkey配置错误导致推送证书不匹配

## 问题原因

代码中配置的appkey与云信控制台后台配置的appkey不一致，导致推送证书无法匹配

## 解决方案

检查并确保代码中配置的appkey与云信控制台后台配置的appkey完全一致。

## 其他触发场景

（合并时在此处追加）
