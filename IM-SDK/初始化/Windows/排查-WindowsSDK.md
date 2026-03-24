---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Windows
title: Windows SDK初始化报错LoadLibraryA error 126
root_cause: 缺少动态库文件，bin目录中的DLL没有拷贝到可执行文件所在目录
solution: 将bin目录中用到的动态库文件拷贝到可执行文件所在目录
customers: ["湖南腾速科技"]
source: chat_history
tags: ["LoadLibraryA", "error 126", "Windows", "动态库", "初始化"]
created: 2025-02-06
updated: 2026-03-20
---

## 问题：Windows Windows SDK初始化报错LoadLibraryA error 126

## 问题详情

**现象**：
Windows集成SDK时在初始化时报错，错误信息为LoadLibraryA error: 126，在nim_chatroom::ChatRoom::Init时报错。

## 排查过程

1. 客户自行排查发现原因 → 没有将bin目录中用到的动态库文件拷贝到可执行文件所在目录

## 问题原因

缺少动态库文件，bin目录中的DLL没有拷贝到可执行文件所在目录

## 解决方案

将bin目录中用到的动态库文件拷贝到可执行文件所在目录

## 其他触发场景
- [Windows] Windows SDK初始化报错LoadLibraryA error 126，来源：['湖南腾速科技']，2026-03-20
- [Windows] Windows SDK初始化报错LoadLibraryA error 126，来源：['湖南腾速科技']，2026-03-20

