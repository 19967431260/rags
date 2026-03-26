---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Windows
title: PC端某些域名图片无法显示
root_cause: PC端SDK版本3.1.0过旧，没有兼容nim-nosdn.netease.im这个新域名
solution: 修改展示方式，采用先下载然后再展示的方式可以临时解决。最终建议升级PC端SDK版本
customers: ["FVIP云信-智业互联健康科技"]
source: chat_history
tags: ["Windows", "图片显示", "域名", "SDK版本"]
created: 2025-08-07
updated: 2025-03-25
---

## 问题：PC端某些域名图片无法显示

## 问题详情

**现象**：
PC客户端https://nim-nosdn.netease.im/这种图片显示不了，http://nim.nos.netease.com这种可以。现象：PC端主动发送的图片正常，其他端发送到PC端的图片显示不了，两个域名不一样

**复现步骤**：
1. 其他端发送图片到PC端
2. PC端显示不了该图片
3. 但PC端主动发送的图片可以正常显示

## 排查过程

1. 客户提供URL进行测试 → 浏览器可以打开
2. 确认是用户反馈的问题 → PC端对PC端可以，其他端发送到PC端不行
3. 文件域名不同 → 怀疑是SDK版本导致
4. 确认PC端SDK版本 → 是3.1.0（2016年版本）
5. 建议升级SDK版本
6. 客户问有没有其他临时办法修复

**关键发现**：PC端SDK版本3.1.0过旧，没有兼容nim-nosdn.netease.im这个新域名

## 问题原因

PC端SDK版本3.1.0过旧，没有兼容nim-nosdn.netease.im这个新域名。

## 解决方案

修改展示方式，采用先下载然后再展示的方式可以临时解决。最终建议升级PC端SDK版本。

## 其他触发场景

- [Windows] PC端某些域名图片无法显示，来源：FVIP云信-智业互联健康科技，2025-03-25
