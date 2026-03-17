---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: 客户端设置pushPayload被第三方回调覆盖导致离线推送失败
root_cause: 第三方回调在modifyResponse中修改了pushPayload，将客户端配置的内容覆盖为{nim:2}，导致离线推送缺少channel_id信息
solution: 第三方回调不要整个替换pushPayload，需要先读取客户端原始配置的内容，然后加上{nim:2}键值对后返回。由于第三方回调设计初衷是内容审核，不会抄送原始pushPayload，建议客户端通过setRemoteExtension将pushPayload内容也放到扩展字段中，服务端通过ext获取后组装完整的pushPayload返回。
customers: ["北京兔玩在线"]
source: chat_history
tags: ["pushPayload", "第三方回调", "modifyResponse", "离线推送", "channel_id", "小米"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Android 客户端设置pushPayload被第三方回调覆盖导致离线推送失败

## 问题详情

**现象**：
客户通过setPushPayload动态设置channel_id后，小米推送收不到离线消息。客户端断点确认pushPayload已传入{"oppoField":"{\"channel_id\":\"push_oplus_category_content\"}","channel_id":"143245"}，但服务端记录只有{"nim":"2"}。

## 排查过程

1. 检查客户端setPushPayload调用 → 断点确认已传入完整的pushPayload数据
2. 检查服务端历史记录 → 发现pushPayload只有{"nim":"2"}，与客户端传入不一致
3. 检查SDK日志 → 发现第三方回调返回"response.body":"{\"errCode\":0,\"modifyResponse\":{\"attach\":\"...\",\"pushPayload\":{\"nim\":\"2\"}}}"

**关键发现**：客户开启了第三方回调，服务端在回调中将pushPayload整个改成了{nim:2}，导致客户端配置的channel_id被覆盖

## 问题原因

第三方回调在modifyResponse中修改了pushPayload，将客户端配置的内容覆盖为{nim:2}，导致离线推送缺少channel_id信息

## 解决方案

第三方回调不要整个替换pushPayload，需要先读取客户端原始配置的内容，然后加上{nim:2}键值对后返回。由于第三方回调设计初衷是内容审核，不会抄送原始pushPayload，建议客户端通过setRemoteExtension将pushPayload内容也放到扩展字段中，服务端通过ext获取后组装完整的pushPayload返回。

## 其他触发场景

（暂无）
