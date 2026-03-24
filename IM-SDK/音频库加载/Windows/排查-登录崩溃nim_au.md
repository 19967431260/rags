---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 音频库加载
platform: Windows
title: 登录崩溃nim_audio.dll加载失败
root_cause: 部分用户系统缺少MSVC运行时库，导致nim_audio.dll无法加载
solution: 安装微软Visual C++运行时库vc_redist.x64.exe，可参考demo安装包中的运行时库安装逻辑
customers: ["VIP云信-广州敬汕贸易有限公司"]
source: chat_history
tags: ["崩溃", "nim_audio.dll", "运行时库", "Windows", "登录"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：Windows 登录崩溃nim_audio.dll加载失败

## 问题详情

**现象**：
Windows端部分用户登录时崩溃，日志显示加载音频库返回nullptr，nim_audio.dll加载失败。

## 排查过程

1. 分析崩溃日志发现加载nim_audio.dll失败
2. 确认是运行时库缺失问题
3. 需要安装MSVC运行时库

## 问题原因

部分用户系统缺少MSVC运行时库，导致nim_audio.dll无法加载

## 解决方案

安装微软Visual C++运行时库vc_redist.x64.exe，可参考demo安装包中的运行时库安装逻辑

## 其他触发场景
- [Windows] 登录崩溃nim_audio.dll加载失败，来源：['VIP云信-广州敬汕贸易有限公司']，2026-03-20

