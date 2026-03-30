---
track_type: "排查类"
sub_type: "客户环境问题"
product: "IM-SDK"
feature: "后台服务"
platform: "Android"
title: "Google Pixel手机上划关闭应用进程无法彻底关闭"
root_cause: "海外手机(Google Pixel)侧滑操作不会结束进程是系统行为，与SDK服务无关"
solution: "这是海外手机系统行为，如需彻底关闭进程可主动调用退出当前进程的代码，对SDK服务没有影响"
customers: ["北京嗨看球科技有限公司"]
source: "chat_history"
tags: ["Google Pixel", "杀进程", "后台服务", "Android", "海外手机"]
created: "2025-09-28"
updated: "2026-03-20"
---

## 问题：Android Google Pixel手机上划关闭应用进程无法彻底关闭

## 问题详情

**现象**：
客户使用Google Pixel 6测试发现，应用运行后上划关闭应用进程功能无法彻底关闭应用，注释掉云信SDK初始化后正常。

## 排查过程

1. 客户反馈Google Pixel手机上划无法彻底杀死进程
2. 确认已配置SDKOption.disableAwake为true
3. 分析日志发现进程被系统清理而非主动杀死
4. 确认海外手机侧滑操作不会结束进程是系统行为

## 问题原因

海外手机(Google Pixel)侧滑操作不会结束进程是系统行为，与SDK服务无关

## 解决方案

这是海外手机系统行为，如需彻底关闭进程可主动调用退出当前进程的代码，对SDK服务没有影响

## 其他触发场景
