---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 服务端录制
platform: Linux
title: Linux服务端录制SDK初始化无日志问题
root_cause: 录制工程进程未正常启动或SDK初始化未执行到
solution: 在录制工程中增加埋点日志，确认API调用路径；检查进程启动状态和网络连通性
customers: ['ISV云信-北京易诚互动-华侨银行']
source: chat_history
tags: ['NERecord', '录制', 'SDK初始化', '无日志', 'Linux']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Linux Linux服务端录制SDK初始化无日志问题

## 问题详情

**现象**：
客户反馈开始录制接口返回成功，但SDK没有生成日志也没有录制视频。排查发现录制工程进程可能未启动或SDK初始化未执行。

## 排查过程

1. 确认SDK日志文件不存在，说明初始化未执行
2. 检查录制工程进程是否启动
3. 建议在录制工程中增加埋点日志，确认createNERecordEngine和initialize API调用情况
4. 排查网络连通性，telnet域名有时不通

## 问题原因

录制工程进程未正常启动或SDK初始化未执行到

## 解决方案

在录制工程中增加埋点日志，确认API调用路径；检查进程启动状态和网络连通性

## 其他触发场景

（合并时在此处追加）
