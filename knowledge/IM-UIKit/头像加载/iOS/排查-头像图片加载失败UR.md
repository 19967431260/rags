---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 头像加载
platform: iOS
title: 头像图片加载失败，URL拼接错误
root_cause: 更新用户资料时头像URL拼接错误，导致URL中包含重复的协议和域名
solution: 检查更新资料时的头像URL设置，避免重复拼接域名。正确格式应为相对路径或完整URL，不要重复添加https://和域名前缀
customers: ["VIP云信-广州品爱科技"]
source: chat_history
tags: ["头像加载", "URL错误", "iOS", "NSURLErrorDomain"]
created: 2025-02-26
updated: 2026-03-20
---

## 问题：iOS 头像图片加载失败，URL拼接错误

## 问题详情

**现象**：
iOS端头像图片加载不出来，报错NSURLErrorDomain Code=-1003，提示未能找到使用指定主机名的服务器。

## 排查过程

1. 检查错误日志发现URL异常
2. 发现URL中两次出现https和域名拼接
3. 检查资料更新逻辑，发现更新头像时多拼接了一次域名

## 问题原因

更新用户资料时头像URL拼接错误，导致URL中包含重复的协议和域名

## 解决方案

检查更新资料时的头像URL设置，避免重复拼接域名。正确格式应为相对路径或完整URL，不要重复添加https://和域名前缀

## 其他触发场景
- [iOS] 头像图片加载失败，URL拼接错误，来源：['VIP云信-广州品爱科技']，2026-03-20
- [iOS] 头像图片加载失败，URL拼接错误，来源：['VIP云信-广州品爱科技']，2026-03-20

