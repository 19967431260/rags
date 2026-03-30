:::::: div custom-tabs
::: tab Android
- 手动登录：
    调用 [`login`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service.html#a39e977dd3a0c0dfe84a6b2dc6c153b11) 方法登录时，判断是否触发 `onSuccess` 回调。
- 自动登录：
    调用 [`observeOnlineStatus`](https://doc.yunxin.163.com/docs/interface/messaging/android/doxygen/Latest/zh/interfacecom_1_1netease_1_1nimlib_1_1sdk_1_1auth_1_1_auth_service_observer.html#adf734324bdc99f79b88aaba8899e76ab) 注册在线状态变化回调，监听当前账户登录状态的变化。 
:::
::: tab iOS
- 手动登录：
    调用 [`login`](https://doc.yunxin.163.com/docs/interface/messaging/iOS/doxygen/Latest/zh/d9/d16/protocol_n_i_m_login_manager-p.html#a7dedc10fcbadf36fb66ce9cc9710b8f6) 方法登录时，判断`error == nil` 表示登录成功。
- 自动登录  
    注册 [`NIMLoginManagerDelegate.–onLogin:`]() 回调监听当前账户登录状态的变化。
:::
::: tab macOS/Windows
- 手动登录：
    调用 [`Login`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a0e8d4b3f4cfcad3cd4bdffd98bdba4c4) 方法登录时，在回调函数`LoginCallback`中，判断 `LoginRes`：其中 `login_step_` 值为 `kNIMLoginStepLogining` 且 `	res_code_` 为 `kNIMResSuccess = 200` 表示登录成功。
- 自动登录：
    与手动登录一致。
:::
::: tab Web
- 手动登录：
    调用 [`NIM.getInstance`](https://doc.yunxin.163.com/messaging/api-refer/web/typedoc/Latest/zh/NIM/classes/nim.NIM.html#getInstance) 方法初始化 SDK 时，SDK 会自动登录，判断是否出发 `onConnect` 回调。
- 自动登录：
    与手动登录一致。
:::
::::::
