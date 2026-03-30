

本文介绍如何实现注销 IM 登录。

## 功能介绍

注销 IM 登录（即登出）后，用户将不再接收 IM 的消息。如果应用退出时 IM 仍处于登录状态，请手动调用 `Client::Logout` 接口登出。

## 实现方法

用户登出应用（注销自己的账号）时需要调用[`Logout`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/classnim_1_1_client.html#a89b02b791521b19c0376c5b9da7a0234)方法。

登出过程因为涉及到和云信服务端的交互以及需要将缓存中的数据持久化到本地，因此回调通知会有 1s 到 20s 左右的延迟。因此会需要上层界面等待的情况，开发者可以通过暂时隐藏  UI，让进程等待退出完成的回调后再执行清理 SDK，退出程序的工作。


登出类型通过 [`NIMLogoutType`](https://doc.yunxin.163.com/docs/interface/messaging/pc/doxygen/Latest/zh/nim__client__def_8h.html#af9ebdfa676ebb89430b15de472f52081) 来定义：

枚举值|说明
-----|-------|
`kNIMLogoutChangeAccout` 	|注销/切换帐号（返回到登录界面）
`kNIMLogoutKickout` 	|被踢（返回到登录界面）
`kNIMLogoutAppExit` 	|程序退出
`kNIMLogoutRelogin` 	|重连操作，包括保存密码时启动程序伪登录后的重连操作以及掉线后的重连操作（帐号未变化）



示例代码如下：

```c++
void LoginCallback::OnLogoutCallback(nim::NIMResCode res_code)
{
	// process logout event
	...
	// note 请勿在该回调中调用 Client::Cleanup，会导致死锁。Cleanup 应该始终在用户主线程执行
}

void foo()
{
	//登出到登录界面(nim::kNIMLogoutChangeAccout) 或者 退出程序(nim::kNIMLogoutAppExit)
	nim::Client::Logout(nim::kNIMLogoutAppExit, &OnLogoutCallback);
}
```