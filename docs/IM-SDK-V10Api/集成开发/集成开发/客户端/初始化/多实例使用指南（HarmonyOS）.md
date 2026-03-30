本文主要介绍如何在 HarmonyOS 项目中使用多个 SDK 实例。

## 功能概述

自 V10.9.75 版本起，NIM HarmonyOS SDK 支持在同一应用中创建多个独立的 SDK 实例，每个实例拥有独立的账号体系、连接通道和数据存储。通过多实例功能，您可以实现同时登录多个账号、无缝切换账号等高级功能。

**典型应用场景：**

- 同时登录多个 IM 账号。
- 账号切换时保持旧账号的消息监听。
- 多 Appkey 应用架构。

**功能特性：**

各实例完全独立，互不影响。

| 资源 | 隔离说明 |
| ------|----------|
| 登录状态 | 各实例独立登录/登出 |
| 事件监听 | 事件回调只触发到对应实例 |
| 消息收发 | 消息只发送到对应账号 |
| 本地存储 | 数据库文件按实例隔离 |
| 网络连接 | 各实例独立维护长连接 |

## 开发环境

在开始集成前，请确保您的开发环境满足以下要求：

- HarmonyOS SDK API 9 及以上
- DevEco Studio 4.0 及以上
- NIM SDK 版本 10.9.75 及以上

## 注意事项

在使用多实例功能时，请注意以下事项：

- **资源消耗**：每个实例独立占用网络连接、内存缓存和本地存储，建议根据实际需求控制实例数量，具体示例请参考 [实例资源管理](#实例资源管理)。
- **推送限制**：一个应用只能存在一个离线推送配置，后设置的会覆盖先设置的。
- **多端登录**：同一账号在不同实例登录受服务端多端登录策略限制，可能导致其中一端被踢下线。
- **及时销毁**：不再使用的实例应及时销毁，避免资源浪费。

## SDK 实例管理

### 创建 SDK 实例

调用 [`NIM.getInstance()`](https://doc.yunxin.163.com/messaging2/client-apis/DEzNTA4OTc?platform=client#getInstance) 方法创建 SDK 实例，每个实例需要指定唯一的 `instanceId`。

::: note note
- `instanceId` 相同时返回同一个实例引用，不会重复创建。
- 避免在 `instanceId` 中使用特殊字符或空字符串，具体请参考 [instanceId 命名规范](#命名规范)。
:::

```typescript
import NIM from '@nimsdk/core';

// 创建第一个实例
const nim1 = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'user1'  // 可选，默认为 'default'
});

// 创建第二个实例
const nim2 = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'user2'
});
```

### 获取已创建的实例

调用 [`NIM.getInstance()`](https://doc.yunxin.163.com/messaging2/client-apis/DEzNTA4OTc?platform=client#getInstance) 方法获取已创建的实例，无需重复传入初始化参数。

```typescript
// 通过 instanceId 获取
const nim1 = NIM.getInstance({ instanceId: 'user1' });

// 获取默认实例
const defaultNim = NIM.getInstance();
```

### 销毁 SDK 实例

不再使用的实例应及时销毁，释放相关资源。

调用 [`NIM.destroyAllInstances()`](https://doc.yunxin.163.com/messaging2/client-apis/DEzNTA4OTc?platform=client#destroyAllInstances) 方法销毁 SDK 实例。

::: note note
- 销毁实例前建议先执行登出操作。
- 销毁后可以使用相同 `instanceId` 创建新实例。
- 应用退出时应清理所有实例避免资源泄漏。
:::

```typescript
// 销毁指定实例
NIM.destroyInstance('user1');

// 销毁所有实例
NIM.destroyAllInstances();
```

## 最佳实践

### 场景一：多账号同时在线

实现一个支持多账号登录的管理器，方便统一管理多个 IM 账号。

```typescript
class MultiAccountManager {
  private instances = new Map<string, NIM>();

  /**
   * 添加并登录新账号
   */
  async addAccount(accountId: string, token: string): Promise<void> {
    const nim = NIM.getInstance({
      appkey: 'your-appkey',
      instanceId: accountId
    });
    
    await nim.V2NIMLoginService.login(accountId, token);

    // 注册消息监听
    nim.V2NIMMessageService.on('onReceiveMessages', (messages) => {
      console.log(`[${accountId}] received:`, messages);
    });
    
    this.instances.set(accountId, nim);
  }

  /**
   * 移除并登出账号
   */
  async removeAccount(accountId: string): Promise<void> {
    const nim = this.instances.get(accountId);
    if (nim) {
      await nim.V2NIMLoginService.logout();
      NIM.destroyInstance(accountId);
      this.instances.delete(accountId);
    }
  }

  /**
   * 获取指定账号的实例
   */
  getAccount(accountId: string): NIM | undefined {
    return this.instances.get(accountId);
  }
}
```

### 场景二：账号无缝切换

实现账号切换功能，切换时不销毁旧实例，保持消息监听。

```typescript
class AccountSwitcher {
  private currentId: string | null = null;

  /**
   * 切换到指定账号
   */
  async switchTo(accountId: string, token: string): Promise<void> {
    // 新账号登录（不销毁旧实例）
    const nim = NIM.getInstance({
      appkey: 'your-appkey',
      instanceId: accountId
    });
    
    await nim.V2NIMLoginService.login(accountId, token);
    
    // 登出旧账号
    if (this.currentId && this.currentId !== accountId) {
      const oldNim = NIM.getInstance({ instanceId: this.currentId });
      await oldNim.V2NIMLoginService.logout();
      NIM.destroyInstance(this.currentId);
    }
    
    this.currentId = accountId;
  }

  /**
   * 获取当前激活的实例
   */
  getCurrentInstance(): NIM | null {
    if (!this.currentId) return null;
    return NIM.getInstance({ instanceId: this.currentId });
  }
}
```

### 场景三：前后台实例分离

创建专门的前台和后台实例，分别处理用户交互和数据同步。

```typescript
// 前台交互实例
const foregroundNim = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'foreground'
});

// 后台同步实例
const backgroundNim = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'background'
});

// 前台处理用户交互
foregroundNim.V2NIMMessageService.on('onReceiveMessages', (messages) => {
  updateUI(messages);
});

// 后台静默同步数据
backgroundNim.V2NIMMessageService.on('onReceiveMessages', (messages) => {
  syncToLocalDB(messages);
});
```

## 相关参考

### 实例资源管理

在使用多实例功能时，由于每个实例独立占用网络连接、内存缓存和本地存储，建议根据实际需求控制实例数量。

```typescript
// 推荐：使用完毕后及时销毁
async function temporaryTask(accountId: string, token: string) {
  const nim = NIM.getInstance({
    appkey: 'your-appkey',
    instanceId: `temp-${accountId}`
  });
  
  try {
    await nim.V2NIMLoginService.login(accountId, token);
    // 执行任务...
  } finally {
    await nim.V2NIMLoginService.logout();
    NIM.destroyInstance(`temp-${accountId}`);
  }
}
```

### 生命周期管理

```typescript
// 应用启动
async function onAppStart() {
  // 恢复主账号实例
  const nim = NIM.getInstance({
    appkey: 'your-appkey',
    instanceId: 'main'
  });
  await nim.V2NIMLoginService.login(savedAccountId, savedToken);
}

// 应用退出
async function onAppExit() {
  // 清理所有实例
  const ids = NIM.getInstanceIds();
  for (const id of ids) {
    const nim = NIM.getInstance({ instanceId: id });
    await nim.V2NIMLoginService.logout();
  }
  NIM.destroyAllInstances();
}
```

<a id="命名规范"></a>

### instanceId 命名规范

| ✅ 推荐 | ❌ 不推荐 |
|--------|----------|
| `'user_123456'` | `'!!@#$'` |
| `'main-account'` | `''` (空字符串) |
| `'tenant-A'` | 包含空格的字符串 |

- 使用有意义的标识，便于调试和管理。
- 避免使用特殊字符。
- 建议使用账号 ID 或业务标识作为 `instanceId`。

## 常见问题

### 同一个 instanceId 多次调用 getInstance 会创建多个实例吗？

不会。相同 `instanceId` 返回同一个 SDK 实例。

```typescript
const nim1 = NIM.getInstance({ instanceId: 'test' });
const nim2 = NIM.getInstance({ instanceId: 'test' });
console.log(nim1 === nim2); // true
```

### 销毁实例后能否重新创建？

可以。销毁后使用相同 `instanceId` 会创建新实例。

```typescript
NIM.destroyInstance('test');
const nim = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'test'  // 创建新实例
});
```

### 不同实例能否使用相同账号登录？

理论上支持，但并不建议。因为同一账号多端登录受服务端策略限制，可能导致其中一端被踢下线。

### 不同实例能否实现不同离线推送？

不能。一个应用只能存在一个推送，后设置的会覆盖先设置的。