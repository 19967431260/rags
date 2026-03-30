本文罗列了网易云信智能体平台的 API 列表及请求 URI。

<style>
table th:first-of-type {width: 25%;}
</style>

## 智能体管理

| 接口 | 请求 URI |
| ---- | ---- |
| [创建智能体](https://doc.yunxin.163.com/ai-hardware/server-apis/DEzNzA1Mjg?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/agent` |
| [查询智能体信息](https://doc.yunxin.163.com/ai-hardware/server-apis/DQzMjI5NTI?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/agent/{agentId}` |
| [查询智能体列表](https://doc.yunxin.163.com/ai-hardware/server-apis/TM2MDUxNzY?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/agent` |
| [更新智能体](https://doc.yunxin.163.com/ai-hardware/server-apis/TU1NjAwNzQ?platform=client) | `PATCH https://rtc-agent.yunxinapi.com/v1/agent/{agentId}` |
| [禁用智能体](https://doc.yunxin.163.com/ai-hardware/server-apis/TkwNzk1OTU?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/agent/disable` |
| [启用智能体](https://doc.yunxin.163.com/ai-hardware/server-apis/DE3NTQ2ODk?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/agent/enable` |
| [删除智能体](https://doc.yunxin.163.com/ai-hardware/server-apis/zU0NTY1NDk?platform=client) | `DELETE https://rtc-agent.yunxinapi.com/v1/agent/{agentId}` |

## 设备授权码

| 接口 | 请求 URI |
| ---- | ---- |
| [激活授权码 License](https://doc.yunxin.163.com/ai-hardware/server-apis/zU3NDcxMTc?platform=client) | `POST https://nrtc-plugins.yunxinapi.com/v2/license/activate` |
| [查询授权码 License](https://doc.yunxin.163.com/ai-hardware/server-apis/DA0ODA0OTc?platform=client) | `POST https://nrtc-plugins.yunxinapi.com/v2/license/query` |

## 设备管理

| 接口 | 请求 URI |
| ---- | ---- |
| [注册设备](https://doc.yunxin.163.com/ai-hardware/server-apis/jk0NTUxNDg?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/device/register`|
| [解绑设备](https://doc.yunxin.163.com/ai-hardware/server-apis/TQwMzc1MzQ?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/device/delete`|
| [更新设备绑定信息](https://doc.yunxin.163.com/ai-hardware/server-apis/DA2MjAyMjQ?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/device/update`|
| [获取设备列表](https://doc.yunxin.163.com/ai-hardware/server-apis/Tg1NDQ4OTY?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/device/list`|
| [按设备 ID 获取设备](https://doc.yunxin.163.com/ai-hardware/server-apis/zMwMjkxNDA?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/device/getDevice`|

## 用户管理

| 接口 | 请求 URI |
| ---- | ---- |
| [新增用户](https://doc.yunxin.163.com/ai-hardware/server-apis/TQyNTM4NDg?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/ai_users` |
| [更新用户](https://doc.yunxin.163.com/ai-hardware/server-apis/zc4NzU3MTI?platform=client) | `PUT https://rtc-agent.yunxinapi.com/v1/ai_users/{uid}` |
| [查询用户信息](https://doc.yunxin.163.com/ai-hardware/guide/zAzOTQ5ODA?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/ai_users/{uid}` |
| [查询用户列表](https://doc.yunxin.163.com/ai-hardware/server-apis/Dc2MDExMjk?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/ai_users` |
| [删除用户](https://doc.yunxin.163.com/ai-hardware/server-apis/DQ5MTE5NDY?platform=client) | `DELETE https://rtc-agent.yunxinapi.com/v1/ai_users/{uid}` |

## 声纹管理

| 接口 | 请求 URI |
| ---- | ---- |
| [添加声纹信息](https://doc.yunxin.163.com/ai-hardware/server-apis/jU4Mjc4NTA?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/voice_prints` |
| [导入声纹信息](https://doc.yunxin.163.com/ai-hardware/server-apis/DQyMzI4ODE?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/voice_prints/add_from_url` |
| [查询声纹信息](https://doc.yunxin.163.com/ai-hardware/server-apis/jEzMzE2MDM?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/voice_prints` |
| [删除声纹信息](https://doc.yunxin.163.com/ai-hardware/server-apis/jM4MDA5NzQ?platform=client) | `DELETE https://rtc-agent.yunxinapi.com/v1/voice_prints/{voicePrintId}` |

## 历史对话

| 接口 | 请求 URI |
| ---- | ---- |
| [导入历史对话](https://doc.yunxin.163.com/ai-hardware/server-apis/TkzNDg0MDg?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/messages/import` |
| [查询历史对话](https://doc.yunxin.163.com/ai-hardware/server-apis/zM3NDUyMzY?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/messages` |

## 设备唤醒词

| 接口 | 请求 URI |
| ---- | ---- |
| [设置设备唤醒词](https://doc.yunxin.163.com/ai-hardware/server-apis/TE2MjM0Nzk?platform=client) | `POST https://rtc-agent.yunxinapi.com/v1/device/updateSdkConfig` |

## 上下文记忆

| 接口 | 请求 URI |
| ---- | ---- |
| [查询上下文记忆](https://doc.yunxin.163.com/ai-hardware/server-apis/zkxOTUyMDc?platform=client) | `GET https://rtc-agent.yunxinapi.com/v1/memories` |


<!--

| [API 概览](https://doc.yunxin.163.com/ai-hardware/server-apis/Tk2OTU2MDg?platform=client) | `API 概览` |
| [错误码](https://doc.yunxin.163.com/ai-hardware/server-apis/DY5MDEzOTQ?platform=client) | `错误码` |
| [调用方式](https://doc.yunxin.163.com/ai-hardware/server-apis/DYwNTk5MzM?platform=client) | `调用方式` | -->