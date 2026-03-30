---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: HarmonyOS
title: 华为手机离线推送收不到certificate fingerprint empty
root_cause: 问题设备的打包签名证书或agconnect-services.json与其他能收到推送的设备不一致，导致生成推送证书失败，报错certificate fingerprint empty
solution: 检查问题设备的打包签名证书和agconnect-services.json文件，确保与其他能正常接收推送的设备使用相同的配置。
customers: ['广西珍心传媒']
source: chat_history
tags: ['华为推送', 'HarmonyOS', 'certificate fingerprint', '离线推送', 'agconnect-services.json']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：HarmonyOS 华为手机离线推送收不到certificate fingerprint empty

## 问题详情

**现象**：
华为应用商店已上架，其他华为手机都能收到离线推送，但特定型号手机收不到离线推送。

## 排查过程

1. 客户反馈特定型号华为手机收不到离线推送
2. 技术支持要求提供SDK日志
3. 查看日志发现华为返回错误：缺少华为的指纹证书
4. 建议检查华为后台指纹证书配置
5. 客户确认已配置指纹证书
6. 其他手机能收到推送，但特定型号不行
7. 技术支持对比正常设备和问题设备的日志
8. 发现正常设备走在线提醒，问题设备生成推送证书失败
9. 最终根因：问题设备的打包签名证书或agconnect-services.json与其他设备不一致

## 问题原因

问题设备的打包签名证书或agconnect-services.json与其他能收到推送的设备不一致，导致生成推送证书失败，报错certificate fingerprint empty

## 解决方案

检查问题设备的打包签名证书和agconnect-services.json文件，确保与其他能正常接收推送的设备使用相同的配置。

## 其他触发场景

（合并时在此处追加）
