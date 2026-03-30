

本文介绍如何管理 IM 实例与 IM 服务端的长连接，即 IM 的登录状态。 



## 功能介绍



IM 实例初始化的同时会与 IM 服务端建立长连接，长连接成功建立则 IM 登录成功。若登录成功，可在初始化时设置的`onconnect`回调中得到相应的登录信息。若登录失败，可在`ondisconnect`回调中获得相应的失败信息。


换言之，**仅首次登录需要在初始化时执行**，后续的登出和重新登录，都需调用相应的接口实现，具体见下文。



## 实现方法
### 登出 IM 



初始化 SDK 后，如果与 IM 服务端成功建立长连接（收到`onconnect`回调函数），可以调用[`nim.disconnect`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#disconnect)方法登出 IM。



::: note note 
- 调用 `nim.disconnect`后，建议再调用[`destroy`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#destroy)方法销毁实例，避免再次重连获取不到完整的最近会话。
- 登出 IM 后可以调用[`nim.connect`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#connect)方法重新登录 IM。
::: 


### 销毁 IM 实例

NIM SDK 实例均为单例模式，但可以调用[`destroy`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#destroy)方法销毁内存中记录的 SDK 实例，同时断开长连接。销毁后，内存消息记录及时间戳将清除，方便开发者做到干净重连。

``` javascript
  var nim = NIM.getInstance({...})
  // 清除实例
  nim.destroy({
    done: function (err) {
      console.log('实例已被完全清除')
    }
  })
````

::: note notice
手动调用 `nim.disconnect` 方法或 `nim.destroy` 方法后，会直接触发 SDK 实例的 `ondisconnect` 回调函数，但此时长连接**并未真正销毁**。只有在 `done` 回调函数触发的时候，才能保证长连接真正销毁（`onclose` 状态）。这点对于**微信小程序**尤其重要，因为小程序只有两条长连接可用，如果在前一条长连接没有处于`onClose`状态，会占用长连接资源，导致反复重连或者被踢下线。
:::



### 重新登录 IM 

调用[`nim.connect`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#connect)方法可实现在登出后重新登录 IM。

::: note notice
该方法必须在调用[`nim.disconnect`](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_NIMInterface.NIMInterface.html#disconnect)方法登出 IM 后，才能调用。
:::




## 相关文档


- 初始化并首次登录 IM 相关说明，请参见[初始化并登录 IM](https://doc.yunxin.163.com/messaging/guide/zE0NDY4Njc?platform=web)。
- 多端登录与互踢相关说明，请参见[多端登录与互踢](https://doc.yunxin.163.com/messaging/guide/jIxMjczMzk?platform=web)。