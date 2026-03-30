网易云信即时通讯 SDK（NetEase IM SDK，以下简称 NIM SDK）提供 NIM SDK 实例管理功能，通过多实例功能，您可以实现同时登录多个账号、无缝切换账号等高级功能。

本文介绍多实例相关 API。更多相关功能请参考开发指南文档 [多实例使用指南](https://doc.yunxin.163.com/messaging2/guide/DQ0MjQ1NTM?platform=client)。

## 支持平台

本文内容适用的开发平台或框架如下表所示：

Android | iOS | macOS/Windows | Web/uni-app/小程序 | Node.js/Electron | HarmonyOS
:----: | :----: | :----: | :----: | :----: | :----: |
-️ | -️ | -️ | -️ | - | ✔️️ |

## API 概览

API | 说明 | 起始版本
---- | ---- | ----
[getInstance](#getInstance) | 获取或创建 SDK 实例 | v10.7.5
[destroyInstance](#destroyInstance) | 销毁指定实例 | v10.7.5
[destroyAllInstances](#destroyAllInstances) | 销毁当前所有实例 | v10.7.5
[hasInstance](#hasInstance) | 检查指定实例是否存在 | v10.7.5
[getInstanceIds](#getInstanceIds) | 获取当前已创建的实例 ID 列表 | v10.7.5

## 接口类

### <span id="getInstance">getInstance</span>

**接口描述**

获取或创建 SDK 实例。

::: note note
- `instanceId` 相同时返回同一个实例引用，不会重复创建。
- 避免在 `instanceId` 中使用特殊字符或空字符串。
:::

**参数说明**

```TypeScript
NIM.getInstance(options?): NIM
```

参数名称 | 类型 | 是否必填 | 说明 |
---- | ---- | ---- | ---- |
`options` | Object | 是 | 初始化配置项。 |
 `appkey` | string | 首次创建时必填 | 网易云信应用标识。 |
 `instanceId` | string | 否 | 实例唯一标识，用于区分不同实例。|
 `*` | - | 否 | 其他初始化参数。|

**示例代码**

```TypeScript
// 首次创建需要完整配置
const nim = NIM.getInstance({
  appkey: 'your-appkey',
  instanceId: 'main',
  debugLevel: 'debug'
});

// 后续获取只需 instanceId
const nimRef = NIM.getInstance({ instanceId: 'main' });
```

**返回值**

`NIM` 实例

### <span id="destroyInstance">destroyInstance</span>

**接口描述**

销毁指定实例，释放相关资源。

**参数说明**

```TypeScript
NIM.destroyInstance(instanceId?): void
```

| 参数名称 | 类型 | 是否必填 | 说明 |
| ---- | ---- | ---- | ---- |
| `instanceId` | string | 否 | 需要销毁的实例 ID。 |

**示例代码**

```TypeScript
// 销毁指定实例
NIM.destroyInstance('user1');

// 销毁默认实例
NIM.destroyInstance();
```

**返回参数**

无返回值。

### <span id="destroyAllInstances">destroyAllInstances</span>

**接口描述**

销毁当前存在的所有实例。

**参数说明**

```TypeScript
NIM.destroyAllInstances(): void
```

**示例代码**

```TypeScript
// 应用退出时清理所有实例
NIM.destroyAllInstances();
```

**返回参数**

无。

### <span id="hasInstance">hasInstance</span>

**接口描述**

查询指定实例是否存在。

**参数说明**

```TypeScript
NIM.hasInstance(instanceId?): boolean
```

**示例代码**

```TypeScript
if (NIM.hasInstance('user1')) {
  const nim = NIM.getInstance({ instanceId: 'user1' });
}
```

**返回参数**

是否存在。true：存在；false：不存在

### <span id="getInstanceIds">getInstanceIds</span>

**接口描述**

获取当前已创建的所有实例。

**参数说明**

```TypeScript
NIM.getInstanceIds()
```

**示例代码**

```TypeScript
const ids = NIM.getInstanceIds();
console.log(ids); // ['default', 'user1', 'user2']
```

**返回参数**

实例的标识列表