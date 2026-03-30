如果您曾集成 NIM SDK，且您的项目代码中存在 NIM SDK 实例，请执行如下流程初始化 IM UIKit。


## 前提条件

- 已[导入组件](https://doc.yunxin.163.com/messaging-uikit/guide/TM0ODQxMTM?platform=web)。
- 已[注册云信 IM 账号](https://doc.yunxin.163.com/messaging-uikit/guide/jEyNDg5NTU?platform=web#4-注册-im-账号)，获取 accid 和 token。

## 注意事项

- 在应用生命周期内，只需初始化一次。 
- Provider 内部管理 IM UIKit 与 IM 服务端的连接与断连。如果需要手动连接和断连，请参考[登录登出](https://doc.yunxin.163.com/messaging-uikit/guide/DAxNTg1NjM?platform=web)。
- Provider 内部管理着全局的状态，一般无需开发者关心。如需访问上下文，请参考[全局上下文](https://doc.yunxin.163.com/messaging-uikit/guide/TIzNDI0OTc?platform=web)。



## 步骤1： 引入工厂函数

引入工厂函数`NimKitCoreFactory`。示例代码如下：

```
import { NimKitCoreFactory } from '@xkit-yx/im-kit-ui'
```


## 步骤2：获取 NimKitCore 构造函数

根据您使用的 SDK 版本（将其值设置为`1`），获取 `NimKitCore` 构造函数。示例代码如下：

```
const sdkVersion = 1
const NimKitCore = NimKitCoreFactory(sdkVersion)
```

## 步骤3：初始化 nimKitCore 实例对象


初始化`nimKitCore`实例对象。

```
const nimKitCore = new NimKitCore({
  initOptions,
  otherOptions,
  funcOptions,
})
```

  参数     |  类型  | 必填 |     说明                                                         
:------------|:------|:----|:---------------------------------------------------------------------------------------------------------------------
`initOptions`  | Object | 是   | NIM SDK 初始化参数。详见 [NIM SDK 初始化参数说明](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMInitializeOptions.html)                                                 
`otherOptions` | Object | 否   |  NIM SDK 初始化其他参数。详见 [NIM SDK 其他初始化参数说明](https://doc.yunxin.163.com/messaging-enhanced/api-refer/web/typedoc/Latest/zh/NIM/interfaces/src_NIMInterface.NIMOtherOptions.html)                                             
`funcOptions`  | Object | 否   | 在您使用 NIM SDK 情况下在参数不生效，请忽略该参数。 

## 步骤4：初始化 IM UIKit

1. 根据`nimKitCore`实例对象获取 NIM SDK 实例。示例代码如下：

```
const nimKitCore = new NimKitCore({
  initOptions,
  otherOptions,
  funcOptions,
})

// 获取 NIM SDK 实例，替换您之前的初始化 SDK 逻辑
const nim = nimKitCore.getNIM()
```    
2. 将`nimKitCore`实例对象传入 IM UIKit，初始化 IM UIKit。

  ```

  import React from 'react'
  import { Provider } from '@xkit-yx/im-kit-ui'

  const nimKitCore = new NimKitCore({
    initOptions,
    otherOptions,
    funcOptions,
  })

  const App = () => {
    return (
      <Provider nimKitCore={nimKitCore} initOptions={initOptions}>
        <div className="app">……</div>
      </Provider>
    )
  }
  ```