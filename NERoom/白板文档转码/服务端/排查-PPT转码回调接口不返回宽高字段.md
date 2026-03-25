---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 白板文档转码
platform: 服务端
title: PPT转码回调接口不返回宽高字段
root_cause: PPT转码回调接口(PPTCutCallbackVO)未定义宽高字段
solution: 当前回调接口确实不包含宽高字段，需收到回调后主动调用查询API获取完整信息。
customers: ["智慧树"]
source: chat_history
tags: ["PPT转码", "回调", "宽高", "pageCount", "文档转码"]
created: 2025-05-15
updated: 2025-03-20
---

## 问题：服务端 PPT转码回调接口不返回宽高字段

## 问题详情

**现象**：
客户反馈PPT转码完成后，回调接口返回的数据中没有width和height字段，但查询接口有返回。

## 排查过程

**关键发现**：PPT转码回调接口(PPTCutCallbackVO)未定义宽高字段

## 问题原因

PPT转码回调接口(PPTCutCallbackVO)未定义宽高字段

## 解决方案

当前回调接口确实不包含宽高字段，需收到回调后主动调用查询API获取完整信息。
