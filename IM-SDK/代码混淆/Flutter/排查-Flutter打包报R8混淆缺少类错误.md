---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 代码混淆
platform: Flutter
title: Flutter打包报R8混淆缺少类错误
root_cause: 未添加SDK混淆规则
solution: 添加SDK混淆配置，参考文档：https://doc.yunxin.163.com/messaging/guide/DAyOTkwMDQ?platform=android#代码防混淆
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["R8", "混淆", "Missing class", "Flutter", "打包"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Flutter Flutter打包报R8混淆缺少类错误

## 问题详情

**现象**：
Flutter项目打包release版本时报错：Missing classes detected while running R8，提示缺少com.netease.nimlib相关注解类和sqlcipher、okhttp等第三方库类。

## 问题原因

未添加SDK混淆规则

## 解决方案

添加SDK混淆配置，参考文档：https://doc.yunxin.163.com/messaging/guide/DAyOTkwMDQ?platform=android#代码防混淆

## 其他触发场景

（暂无）
