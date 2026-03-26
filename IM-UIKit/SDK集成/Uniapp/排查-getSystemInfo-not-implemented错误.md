---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: SDK集成
platform: Uniapp
title: Uniapp初始化报getSystemInfo not implemented：去掉isWxApp判断
root_cause: UIKit初始化代码中通过isWxApp判断加载不同配置，但当前环境uni.getSystemInfo未实现导致报错
solution: 去掉isWxApp判断；直接设置lbsUrls和linkUrl参数；lbsUrls: ["https://lbs.netease.im/lbs/wxwebconf.jsp"]，linkUrl: "wlnimsc0.netease.im"；如HBuilderX编译器版本与当前环境不兼容也可能导致此问题
customers: ["北京大成互联"]
source: chat_history
tags: ["Uniapp", "getSystemInfo", "isWxApp", "初始化报错"]
created: 2025-07-10
updated: 2025-07-25
---

## 问题：Uniapp初始化报getSystemInfo not implemented：去掉isWxApp判断

## 问题原因

UIKit初始化代码中通过isWxApp判断加载不同配置，但当前环境uni.getSystemInfo未实现导致报错

## 解决方案

去掉isWxApp判断；直接设置lbsUrls和linkUrl参数；lbsUrls: ["https://lbs.netease.im/lbs/wxwebconf.jsp"]，linkUrl: "wlnimsc0.netease.im"；如HBuilderX编译器版本与当前环境不兼容也可能导致此问题
