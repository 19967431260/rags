---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: HarmonyOS
title: 鸿蒙SDK依赖vendor包导致项目无法运行
root_cause: 依赖路径配置错误，vendor工具类包未正确引入
solution: 对比官方demo的依赖方式进行配置。远端依赖时base库会自动拉取vendor，本地har依赖时需要单独引入vendor包。参考：https://github.com/netease-im/nim-harmony-demo
customers: ['2.0云信-长沙代客', '2_0云信-长沙代客']
source: chat_history
tags: ["依赖配置", "集成问题", "HarmonyOS", "vendor"]
created: 2026-02-25
updated: 2026-03-15
---

## 问题：HarmonyOS 鸿蒙SDK依赖vendor包导致项目无法运行

## 问题详情

**现象**：
在鸿蒙项目中引入IM SDK依赖后，项目无法启动运行。依赖路径配置错误导致无法正确引入vendor工具类包。



## 排查过程



## 问题原因\n\n依赖路径配置错误，vendor工具类包未正确引入

## 解决方案

对比官方demo的依赖方式进行配置。远端依赖时base库会自动拉取vendor，本地har依赖时需要单独引入vendor包。参考：https://github.com/netease-im/nim-harmony-demo
