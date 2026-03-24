---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: UIKit集成
platform: Web
title: 私有化环境UIKit图标资源加载问题
root_cause: SDK内部依赖http://at.alicdn.com/t/c/font_3429868_fwpfhemf2p.js加载图标，内网无法访问外网资源。
solution: 1. 下载iconfont文件到本地内网服务器
2. 初始化时通过localOptions.iconfontUrl配置本地图标URL（数组类型）
3. 建议纯内网环境使用源码集成方式，方便后续自定义修改。
customers: ['云信-宏信动力(北京)科技有限公司']
source: chat_history
tags: ['UIKit', '私有化', '图标', 'iconfont', '内网']
created: 2025-02-12
updated: 2026-03-23
---

## 问题：Web 私有化环境UIKit图标资源加载问题

## 问题详情

**现象**：
私有化内网环境下，UIKit部分图标无法显示，外网环境正常。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 内网环境UIKit表情和部分按钮图标无法显示
2. 外网环境正常
3. 检查网络发现SDK内部依赖了外部iconfont资源

## 问题原因

SDK内部依赖http://at.alicdn.com/t/c/font_3429868_fwpfhemf2p.js加载图标，内网无法访问外网资源。

## 解决方案

1. 下载iconfont文件到本地内网服务器
2. 初始化时通过localOptions.iconfontUrl配置本地图标URL（数组类型）
3. 建议纯内网环境使用源码集成方式，方便后续自定义修改。

## 其他触发场景

（合并时在此处追加：`- [Web] 私有化环境UIKit图标资源加载问题，来源：['云信-宏信动力(北京)科技有限公司']，2026-03-23`）
