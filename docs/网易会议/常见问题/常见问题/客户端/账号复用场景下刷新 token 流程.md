如果您在接入网易会议组件前，已使用 IM 账号体系（存在 IM 账号），那么您需要通过复用 IM 账号流程完成接入。在此场景下，网易会议服务器仅备份 IM 账号以及密码信息，无法主动感知后续 IM 账号的更新操作。因此发生 Token 刷新时，需要按场景进行同步，避免认证不一致。

## case 1：保持 IM 账号 Token 不变，仅刷新会议账号 Token

若仅需要刷新会议账号 Token 且不改变 IM 账号 Token，直接调用会议层 [重置用户令牌](https://doc.yunxin.163.com/meeting/server-apis/zc3MTAyODU?platform=server) 接口即可。

该接口仅更新会议账号关联的 Token，不会修改会议服务器存储的 IM 相关信息，IM 账号 Token 保持原有状态。

## case 2：IM 账号 Token 已刷新，需同步至会议服务器

当 IM 账号 Token 完成更新后，需通过底层房间组件 [更新账号和 Token](https://doc.yunxin.163.com/neroom/server-apis/jQ3MTcxMjY?platform=server) 接口同步更新会议服务器存储的 IM Token 信息，确保账号认证一致性。

调用接口时需在请求体中指定 `im_token` 字段，赋值为更新后的 IM 账号 Token，接口调用后会议服务器将同步存储最新的 IM 账号信息。