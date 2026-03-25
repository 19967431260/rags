---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 音视频通话
platform: Linux
title: Linux Qt demo运行报错，摄像头和屏幕共享都失败
root_cause: 使用root用户编译运行、appkey配置错误、接口调用顺序错误、重复调用接口
solution: 1. 使用非root用户编译和运行；2. 确保appkey配置正确；3. 确保先调用join加入房间再调用屏幕共享接口；4. 检查接口调用顺序，避免重复调用；5. 杀掉进程重新用新uid测试
customers: ["西安优迈智慧矿山科技有限公司"]
source: chat_history
tags: ["音视频2.0","Linux Qt","屏幕共享","摄像头"]
created: 2025-05-23
updated: 2025-03-23
---

## 问题：Linux Linux Qt demo运行报错，摄像头和屏幕共享都失败

## 问题详情

**现象**：
客户运行NEScreenShare-Linux demo时，摄像头打开失败，屏幕共享也失败，报各种错误。

**环境信息**：
- 平台：Linux Qt
- 功能：RTC音视频通话

## 排查过程

1. 确认运行用户 → 是否使用root用户
2. 检查appkey配置 → 确认配置正确
3. 检查接口调用顺序 → 是否先join再加入房间
4. 检查重复调用 → 避免接口重复调用

**关键发现**：多种原因可能导致demo运行失败

## 问题原因

1. 使用root用户编译和运行
2. appkey配置不正确
3. 未先调用join加入房间就调用屏幕共享接口
4. 接口调用顺序错误或重复调用

## 解决方案

1. **使用非root用户**：确保使用非root用户编译和运行
2. **检查appkey配置**：确保appkey配置正确
3. **正确调用顺序**：确保先调用join加入房间再调用屏幕共享接口
4. **避免重复调用**：检查接口调用顺序，避免重复调用
5. **重新测试**：杀掉进程重新用新uid测试

## 其他触发场景

