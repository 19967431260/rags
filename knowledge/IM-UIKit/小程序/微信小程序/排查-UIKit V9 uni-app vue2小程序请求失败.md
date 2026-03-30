---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 小程序
platform: 微信小程序
title: UIKit V9 uni-app vue2小程序请求失败
root_cause: 小程序域名白名单未配置
solution: 将云信域名添加到小程序后台白名单，并在初始化时配置小程序专属域名，参考文档：https://doc.yunxin.163.com/messaging/guide/jUwODczMzI?platform=miniProgram
customers: ['杭州云汽配配科技有限公司']
source: chat_history
tags: ['小程序', 'uni-app', 'vue2', '域名白名单', '网络错误']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：微信小程序 UIKit V9 uni-app vue2小程序请求失败

## 问题详情

**现象**：
UIKit V9 uni-app vue2开发的小程序，请求失败，显示网络错误

## 排查过程



## 问题原因

小程序域名白名单未配置

## 解决方案

将云信域名添加到小程序后台白名单，并在初始化时配置小程序专属域名，参考文档：https://doc.yunxin.163.com/messaging/guide/jUwODczMzI?platform=miniProgram

## 其他触发场景

（合并时在此处追加）
