---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送证书
platform: HarmonyOS
updated: 2025-08-12
---

<!-- entry: platform=HarmonyOS, created=2025-08-12, customers=["信雅达/晋商银行"], source=chat_history, frequency=1, tags=["HarmonyOS", "华为push", "证书配置", "profile"], troubleshooting="1. 客户反馈华为push报错 → 2. 客服确认是否使用鸿蒙NEXT → 3. 客服说明SDK已支持 → 4. 客服询问具体错误码 → 5. 客户确认是app没有申请推送证书", root_cause="客户的app没有申请华为推送证书", solution="需要在华为开发者后台申请推送证书，SDK已支持鸿蒙NEXT的华为push通道，回执状态不需要开通" -->
## Q: 鸿蒙华为push报错profile证书配置错误

**问题描述**：华为反馈鸿蒙NEXT版本的pushService.getToken接口报错profile证书配置错误，每天报错5K+

**排查过程**：
1. 客户反馈华为push报错
2. 客服确认是否使用鸿蒙NEXT
3. 客服说明SDK已支持
4. 客服询问具体错误码
5. 客户确认是app没有申请推送证书

**根因**：客户的app没有申请华为推送证书

**解决方案**：需要在华为开发者后台申请推送证书，SDK已支持鸿蒙NEXT的华为push通道，回执状态不需要开通