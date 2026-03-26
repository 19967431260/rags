---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: WebView权限
platform: 微信小程序
title: WebView拒绝权限后无法再次弹窗
root_cause: 安卓WebView权限策略是静态的，用户拒绝后不会自动再次请求，需要Native层配合处理
solution: 方案1：手动重置app应用权限、清除内容（到应用信息→权限→允许摄像头/麦克风，到应用信息→存储→删除数据）；方案2：让Native代码修改WebView配置，在WebChromeClient的onPermissionRequest中永远自动grant权限绕过WebView的限制
customers: ["杭州三汇"]
source: chat_history
tags: ["WebView", "权限", "微信小程序", "设备检测"]
created: 2025-08-18
updated: 2025-03-25
---

## 问题：WebView拒绝权限后无法再次弹窗

## 问题详情

**现象**：
客户在手机上用谷歌浏览器访问音视频设备检测页面，第一次拒绝授权摄像头和麦克风后，关闭浏览器重新进入页面，不会有授权弹窗

## 排查过程

1. 客户反馈问题现象 → 2. 客服复现确认问题存在 → 3. 研发定位根因：安卓WebView权限策略比较静态且由系统/容器自己管理，用户一旦拒绝就会直接deny，页面里无法再次弹出授权

**关键发现**：安卓WebView权限策略是静态的，用户拒绝后不会自动再次请求

## 问题原因

安卓WebView权限策略是静态的，用户拒绝后不会自动再次请求，需要Native层配合处理。

## 解决方案

方案1：手动重置app应用权限、清除内容（到应用信息→权限→允许摄像头/麦克风，到应用信息→存储→删除数据）

方案2：让Native代码修改WebView配置，在WebChromeClient的onPermissionRequest中永远自动grant权限绕过WebView的限制

## 其他触发场景

- [微信小程序] WebView拒绝权限后无法再次弹窗，来源：杭州三汇，2025-03-25