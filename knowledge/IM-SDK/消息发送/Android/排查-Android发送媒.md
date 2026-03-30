---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: Android发送媒体消息返回code0问题排查
root_cause: 日志显示上传文件失败，可能是设备网络配置或本地缓存问题，卸载重装后恢复
solution: 尝试卸载重装应用，检查设备网络配置是否有特殊限制
customers: ["成都更好玩科技有限公司"]
source: chat_history
tags: ["IM-SDK", "Android", "code0", "媒体消息", "上传失败"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Android Android发送媒体消息返回code0问题排查

## 问题详情

**现象**：
安卓SDK 9.19.3版本发送图片、视频、语音消息callback返回code0，发送文本消息正常。特定设备必现，其他设备正常。

## 排查过程

1. 获取SDK日志分析 → 发现上传文件失败
2. 询问网络环境 → 确认未开VPN
3. 尝试卸载重装 → 问题解决
4. 结论：可能是网络配置或本地缓存导致

## 问题原因

日志显示上传文件失败，可能是设备网络配置或本地缓存问题，卸载重装后恢复

## 解决方案

尝试卸载重装应用，检查设备网络配置是否有特殊限制

## 其他触发场景
- [Android] Android发送媒体消息返回code0问题排查，来源：['成都更好玩科技有限公司']，2026-03-20
- [Android] Android发送媒体消息返回code0问题排查，来源：['成都更好玩科技有限公司']，2026-03-20

