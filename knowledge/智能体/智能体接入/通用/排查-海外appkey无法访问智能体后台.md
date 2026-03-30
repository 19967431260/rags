---
track_type: 排查类
sub_type: 使用问题
product: 智能体
feature: 智能体接入
platform: 通用
title: 海外appkey无法访问智能体后台
root_cause: 海外appkey目前在智能体后台还访问不了，只能走API配置智能体
solution: 重新创建一个应用，IM和RTC都选择国内来体验。海外appkey兼容智能体后台功能正在排期中。海外appkey和国内appkey在用户体验层面差别不大，本质都是就近走边缘节点。
customers: ["福建省云上金时科创有限公司"]
source: chat_history
tags: ["智能体","海外appkey","后台访问","agent not found"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：通用 海外appkey无法访问智能体后台

## 问题详情

**现象**：
客户使用海外appkey（130f9d722cae73c40c439da2f22d7668）登录智能体后台显示空白，提示agent not found。同一账号在不同电脑登录都出现此问题。

## 排查过程

1. 检查浏览器 → 尝试Chrome/Edge/360浏览器均有问题
2. 检查network请求 → 返回空列表
3. 检查appkey类型 → 发现是海外appkey

**关键发现**：海外appkey目前不支持智能体后台访问

## 问题原因

海外appkey目前在智能体后台还访问不了，只能走API配置智能体

## 解决方案

重新创建一个应用，IM和RTC都选择国内来体验。海外appkey兼容智能体后台功能正在排期中。海外appkey和国内appkey在用户体验层面差别不大，本质都是就近走边缘节点。

## 其他触发场景

