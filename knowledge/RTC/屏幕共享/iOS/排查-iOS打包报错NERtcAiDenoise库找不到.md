---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 屏幕共享
platform: iOS
title: iOS打包报错NERtcAiDenoise库找不到
root_cause: 5.6.35版本新增屏幕共享功能，需要额外的库和配置
solution: 如不需要屏幕共享功能，删除5.6.35中带的三个屏幕共享相关文件和package.json中的对应内容后重新打包
customers: ['VIP云信-雨后生活服务（杭州）']
source: chat_history
tags: ['RTC', 'iOS', '打包', 'NERtcAiDenoise', '屏幕共享', 'Uniapp']
created: 2025-02-12
updated: 2026-03-23
---

## 问题：iOS iOS打包报错NERtcAiDenoise库找不到

## 问题详情

**现象**：
客户打包iOS基座时报错，提示framework not found NERtcAiDenoise，去掉NERTC插件能打包成功。

**环境信息**：
- 平台：iOS
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认是新版本5.6.35添加屏幕共享功能导致
2. 需要注册app group
3. 客户已创建APP group并更新profiles仍报错
4. 最终解决方案：删除屏幕共享相关文件

## 问题原因

5.6.35版本新增屏幕共享功能，需要额外的库和配置

## 解决方案

如不需要屏幕共享功能，删除5.6.35中带的三个屏幕共享相关文件和package.json中的对应内容后重新打包

## 其他触发场景

（合并时在此处追加：`- [iOS] iOS打包报错NERtcAiDenoise库找不到，来源：['VIP云信-雨后生活服务（杭州）']，2026-03-23`）
