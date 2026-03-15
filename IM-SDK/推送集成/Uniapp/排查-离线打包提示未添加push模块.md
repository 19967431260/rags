---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送集成
platform: Uniapp
title: 离线打包提示未添加push模块
root_cause: 用户可能在离线打包时引入了uniPush相关配置,导致框架检测到推送模块但未正确配置。云信推送是独立的,不依赖uniPush。
solution: 1. 确认manifest.json中配置了云信推送模块权限 2. 不要集成uniPush相关文件和配置 3. 只需依赖云信推送插件,添加好plugin相关配置即可 4. 可参考官方demo：https://github.com/netease-im/uni-offline-push
customers: ["北京北拓云鹰科技有限公司"]
source: chat_history
tags: ["离线打包", "push模块", "Uniapp", "uniPush", "manifest"]
created: 2026-02-11
updated: 2026-03-15
---

## 问题：Uniapp 离线打包提示未添加push模块

## 问题详情

**现象**：
Uniapp项目使用离线打包方式集成FCM推送,打包后安装到手机运行时提示"打包时未添加push模块"。已依赖云信推送插件。

## 排查过程

1. 用户离线打包后安装APK,启动时提示未添加push模块
2. 确认已依赖云信推送插件
3. 检查manifest.json配置

**关键发现**：提示来自Uniapp框架,不是云信SDK提示;用户可能误集成了uniPush相关配置

## 问题原因

用户可能在离线打包时引入了uniPush相关配置,导致框架检测到推送模块但未正确配置。云信推送是独立的,不依赖uniPush。

## 解决方案

1. 确认manifest.json中配置了云信推送模块权限
2. 不要集成uniPush相关文件和配置（https://nativesupport.dcloud.net.cn/AppDocs/usemodule/androidModuleConfig/push.html中的配置）
3. 只需依赖云信推送插件,添加好plugin相关配置即可
4. 可参考官方demo：https://github.com/netease-im/uni-offline-push

## 其他触发场景
