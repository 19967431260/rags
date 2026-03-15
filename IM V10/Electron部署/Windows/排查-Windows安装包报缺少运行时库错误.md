---
track_type: 排查类
sub_type: 客户环境问题
product: IM V10
feature: Electron部署
platform: Windows
title: Windows安装包报缺少运行时库错误
root_cause: 部分Windows电脑缺少微软运行时库
solution: 安装微软运行时库，并将其放到electron-builder的安装脚本里面自动安装，使用静默安装参数。
customers: ["中讯邮电"]
source: chat_history
tags: ["Electron", "Windows", "运行时库", "安装错误", "electron-builder"]
created: 2026-01-04
updated: 2026-03-15
---

## 问题：Windows Windows安装包报缺少运行时库错误

## 问题详情

**现象**：
客户使用Electron打包的应用，同一个安装包在有的Windows电脑可以安装，有的电脑报缺少运行时库错误。

## 问题原因

部分Windows电脑缺少微软运行时库

## 解决方案

安装微软运行时库，并将其放到electron-builder的安装脚本里面自动安装，使用静默安装参数。

## 其他触发场景

（合并时在此处追加）
