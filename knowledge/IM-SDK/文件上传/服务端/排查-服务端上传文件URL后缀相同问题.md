---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "文件上传"
platform: "服务端"
title: "服务端上传文件URL后缀相同问题"
root_cause: "服务器根据文件名、上传时间、上传token计算URI，如需要自定义URI可自行指定文件名上传"
solution: "关注yunxin/之后的URI部分即可区分不同资源。如需自定义URI文件名，可在上传时自行指定。"
customers: ["圆通IM私有化"]
source: "chat_history"
tags: ["文件上传", "URL", "NOS", "服务端API", "uri"]
created: "2025-09-12"
updated: "2026-03-20"
---

## 问题：服务端 服务端上传文件URL后缀相同问题

## 问题详情

**现象**：
不同文件通过服务端API上传后，URL的后缀部分（文件名）显示相同。

## 排查过程

1. 客户反馈两个不同文件上传后URL后缀相同
2. 查看URL发现yunxin/后的编码段实际不同
3. 客户关注的是URL最后的文件名部分
**关键发现**：URL编码段不同代表不同资源，文件名后缀是服务器根据算法因子计算的

## 问题原因

服务器根据文件名、上传时间、上传token计算URI，如需要自定义URI可自行指定文件名上传

## 解决方案

关注yunxin/之后的URI部分即可区分不同资源。如需自定义URI文件名，可在上传时自行指定。

## 其他触发场景
