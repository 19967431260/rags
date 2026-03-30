本文档介绍如何使用 CallKit 实现单聊呼叫功能，提供完整的 UI 界面和自定义方案。

## 概述

云信呼叫组件是网易云信推出的音视频通话 UI 组件，提供音视频通话场景下常见的 1V1 音视频通话等功能。

## 开发环境

- DevEco Studio 5.0.3.900 及以上版本。
- HarmonyOS SDK API 13 及以上版本。
- Harmony 系统 5.0.0.102 及以上版本的真机。

## 准备工作

根据本文操作前，请确保您已经完成了以下设置：

- 在 [网易云信控制台](https://app.yunxin.163.com/global/home) [创建应用](https://doc.yunxin.163.com/console/concept/TIzMDE4NTA?platform=console)，并获取了对应的 App Key。
- 开通以下服务，若未开通，请参考 [开通服务](https://doc.yunxin.163.com/console/concept/zc3NDYzNzc?platform=console) 进行开通。

    - IM 即时通讯。当使用呼叫组件自带的话单功能时，需开通 IM。
    - 信令。用于实现点对点呼叫邀请以及音视频通话。
    - 音视频通话 2.0。用于实现实时音视频通话。
    - 如需要抄送，请提前开通消息抄送中的 **话单** 抄送服务，实现在一通通话结束后，发送事件通知消息，标记此次通话是否接通以及通话时间、类型等数据。
- 已创建鸿蒙项目，或有可基于的鸿蒙项目。

## 集成步骤

### 步骤一：添加依赖

在项目的 `oh-package.json5` 文件中添加以下依赖，然后执行 `ohpm install` 命令。

```json
{
  "dependencies": {
    "@yunxin/callkit": "4.0.1",
    "@yunxin/callkit_ui": "4.0.1",
    "@nertc/nertc_sdk": "5.9.11",
    "@nimsdk/message": "10.9.50",
    "@nimsdk/user": "10.9.50",
    "@nimsdk/signalling": "10.9.50",
    "@nimsdk/nim": "10.9.50",
    "@nimsdk/base": "10.9.50",
  }
}
```

### 步骤二：配置权限

在 `module.json5` 文件中，添加以下权限：

```json
{
  "requestPermissions": [
    {
      "name": "ohos.permission.MICROPHONE",
      "reason": "用于音视频通话",
      "usedScene": {
        "abilities": ["EntryAbility"],
        "when": "inuse"
      }
    },
    {
      "name": "ohos.permission.CAMERA",
      "reason": "用于视频通话",
      "usedScene": {
        "abilities": ["EntryAbility"],
        "when": "inuse"
      }
    }
  ]
}
```

### 步骤三：初始化 NIM SDK

在初始化呼叫组件前，需要先进行 NIM SDK 的初始化。

```typescript
// IM初始化
NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_MESSAGE, (core, serviceName, serviceConfig) => new V2NIMMessageServiceImpl(core, serviceName, serviceConfig));
NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_USER, (core, serviceName, serviceConfig) => new V2NIMUserServiceImpl(core, serviceName, serviceConfig));
NIMSdk.registerCustomServices(V2NIMProvidedServiceType.V2NIM_PROVIDED_SERVICE_SIGNALLING, (core, serviceName, serviceConfig) => new V2NIMSignallingServiceImpl(core, serviceName, serviceConfig));
this._nim = NIMSdk.newInstance(this._context, initializeOptions, serviceOptions)
```

### 步骤四：初始化并登录呼叫组件

```typescript
// 创建配置对象
const config: NESetupConfig = new NESetupConfig(
  context,                    // common.Context 对象
  nim,                         // NIM SDK 实例
  "your appkey",               // AppKey
  accountId                    // 当前登录的账号ID
);

// 初始化 CallKit 引擎
NECallUI.getInstance().setupEngine(config);

// 登录 CallKit
NECallUI.getInstance().login(
  appKey,        // 云信 APP_KEY
  accountId,     // 账号 ID
  token          // 账号 Token（从业务服务器获取）
);
```

### 步骤五：发起通话

使用 `NECallUI.call()` 方法发起音视频通话：

```typescript
// 创建呼叫参数
const param = new NECallParam(
  'target_account_id',  // 被叫用户账号ID
  NECallType.VIDEO      // 通话类型：NECallType.AUDIO（音频）或 NECallType.VIDEO（视频）
);               

// 可选：设置推送配置
const pushConfig = new NECallPushConfig();
pushConfig.pushEnabled = true;
pushConfig.pushTitle = '来电提醒';
pushConfig.pushContent = '您有一个视频通话';
param.pushConfig = pushConfig;

// 发起呼叫
const result = await NECallUI.getInstance().call(param);
```

### （可选）步骤六：登出

退出登录：

```typescript
NECallUI.getInstance().logout();
```