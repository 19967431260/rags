

您可调用[获取圈组连接地址](https://doc.yunxin.163.com/messaging/docs/DY3NDU0NDU?platform=server)（https://api.yunxinapi.com/nimserver/qchat/requestAddr.action）获取应用客户端与圈组服务端的连接地址。用户登录圈组时，必须传入该连接地址。

本文主要罗列了圈组功能相关的 API 列表。

::: note note 

圈组模块的所有 API 都存在频控：

每个接口在单个应用中默认最高调用频率：100 次/秒，如超限，将被屏蔽 10 秒。若根据业务需要调整部分接口的频控，请通过官网首页右侧的联系方式联系云信商务经理。
:::

## 圈组服务器相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 创建圈组服务器](https://doc.yunxin.163.com/messaging/docs/TE5ODM0MTk?platform=server)                   |https://api.yunxinapi.com/nimserver/qchat/createServer.action                           
|[ 修改圈组服务器信息 ](https://doc.yunxin.163.com/messaging/docs/zQ0OTE4MjE?platform=server)               | https://api.yunxinapi.com/nimserver/qchat/updateServer.action                          
|[ 删除圈组服务器  ](https://doc.yunxin.163.com/messaging/docs/DcxMTA4NjY?platform=server)                  |https://api.yunxinapi.com/nimserver/qchat/removeServer.action                           
|[ 批量查询服务器信息 ](https://doc.yunxin.163.com/messaging/docs/zkwMjUxMzE?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/getServers.action                             
|[ 分页查询服务器列表](https://doc.yunxin.163.com/messaging/docs/Dg4NTEzMTI?platform=server)                |https://api.yunxinapi.com/nimserver/qchat/getServerListPage.action                      

## 圈组服务器成员相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 邀请服务器成员](https://doc.yunxin.163.com/messaging/docs/DI3MDc5ODU?platform=server)                    |https://api.yunxinapi.com/nimserver/qchat/inviteServerMember.action                     
|[ 接受邀请 ](https://doc.yunxin.163.com/messaging/docs/Dk2NDIyNzU?platform=server)                         |https://api.yunxinapi.com/nimserver/qchat/acceptServerInvite.action                     
|[ 拒绝邀请](https://doc.yunxin.163.com/messaging/docs/DAxMDkzMjY?platform=server)                          |https://api.yunxinapi.com/nimserver/qchat/rejectServerInvite.action                     
|[ 申请加入服务器 ](https://doc.yunxin.163.com/messaging/docs/TY1NDQ3NTM?platform=server)                   |https://api.yunxinapi.com/nimserver/qchat/applyServer.action                            
|[ 接受申请](https://doc.yunxin.163.com/messaging/docs/DkwNDkyMjQ?platform=server)                          |https://api.yunxinapi.com/nimserver/qchat/acceptServerApply.action                      
|[ 拒绝申请 ](https://doc.yunxin.163.com/messaging/docs/jIxMjI4Mjc?platform=server)                         |https://api.yunxinapi.com/nimserver/qchat/rejectServerApply.action                      
|[ 生成邀请码 ](https://doc.yunxin.163.com/messaging/docs/TU0Njg5MDE?platform=server)                       |https://api.yunxinapi.com/nimserver/qchat/generateInviteCode.action                     
|[ 通过邀请码加入  ](https://doc.yunxin.163.com/messaging/docs/TMyMzQwNzI?platform=server)                  |https://api.yunxinapi.com/nimserver/qchat/joinServerByInviteCode.action                
|[ 踢出成员      ](https://doc.yunxin.163.com/messaging/docs/jU5MjMwNDU?platform=server)                    |https://api.yunxinapi.com/nimserver/qchat/kickServerMember.action                       
|[ 主动退出服务器   ](https://doc.yunxin.163.com/messaging/docs/DY3NTE5MDY?platform=server)                 | https://api.yunxinapi.com/nimserver/qchat/leaveServer.action                           
|[ 修改自己的成员信息 ](https://doc.yunxin.163.com/messaging/docs/DQyMDI4ODE?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/updateServerMember.action                     
|[ 修改他人的成员信息](https://doc.yunxin.163.com/messaging/docs/jEyMzYyMjg?platform=server)                | https://api.yunxinapi.com/nimserver/qchat/updateOtherServerMember.action               
|[ 分页查询服务器成员列表](https://doc.yunxin.163.com/messaging/docs/jAxMzQ5NjA?platform=server)            |https://api.yunxinapi.com/nimserver/qchat/getServerMemberListPage.action                
|[ 批量查询服务器成员信息](https://doc.yunxin.163.com/messaging/docs/zU1ODIyNzM?platform=server)            | https://api.yunxinapi.com/nimserver/qchat/getServerMembers.action                      
|[ 查询服务器的申请和邀请记录](https://doc.yunxin.163.com/messaging/docs/zkzMjY4MjU?platform=server)        |https://api.yunxinapi.com/nimserver/qchat/queryInviteApplyHistoryByServer.action        
|[ 查询个人的申请和邀请记录](https://doc.yunxin.163.com/messaging/docs/DY1OTcyMTk?platform=server)          |https://api.yunxinapi.com/nimserver/qchat/queryInviteApplyHistoryByUser.action          
|[ 更新成员封禁状态  ](https://doc.yunxin.163.com/messaging/docs/jQyMDI3MTY?platform=server)                |https://api.yunxinapi.com/nimserver/qchat/updateServerMemberBan.action                   
|[ 分页查询封禁成员列表](https://doc.yunxin.163.com/messaging/docs/DU2OTM2ODc?platform=server)              | https://api.yunxinapi.com/nimserver/qchat/getServerMemberBanListPage.action             


## 圈组频道相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 创建频道  ](https://doc.yunxin.163.com/messaging/docs/zQ0MjkxMTA?platform=server)                        |https://api.yunxinapi.com/nimserver/qchat/createChannel.action                          
|[ 修改频道基础信息 ](https://doc.yunxin.163.com/messaging/docs/zI1MTAzMzY?platform=server)                 |https://api.yunxinapi.com/nimserver/qchat/updateChannel.actionC                          
|[ 修改频道分组相关信息](https://doc.yunxin.163.com/messaging/docs/TgyMDE3OTA?platform=server)              |https://api.yunxinapi.com/nimserver/qchat/updateCategoryInfoOfChannel.action             
|[ 删除频道  ](https://doc.yunxin.163.com/messaging/docs/zY4Mjc4NjI?platform=server)                        |https://api.yunxinapi.com/nimserver/qchat/removeChannel.action                          
|[ 分页查询频道列表 ](https://doc.yunxin.163.com/messaging/docs/zQ2OTU4NjA?platform=server)                 |https://api.yunxinapi.com/nimserver/qchat/getChannelListPage.action                     
|[ 批量查询频道信息](https://doc.yunxin.163.com/messaging/docs/zQwOTQ3Njk?platform=server)                  |https://api.yunxinapi.com/nimserver/qchat/getChannels.action                            
|[ 分页查询频道成员列表 ](https://doc.yunxin.163.com/messaging/docs/jU0ODM3MTM?platform=server)             |https://api.yunxinapi.com/nimserver/qchat/getChannelMemberListPage.action               
|[ 修改频道黑白名单成员 ](https://doc.yunxin.163.com/messaging/docs/TUyNzkxOTU?platform=server)             |https://api.yunxinapi.com/nimserver/qchat/updateWhiteBlackIdentifyUser.action           
|[ 修改频道黑白名单身份组 ](https://doc.yunxin.163.com/messaging/docs/TU0NzQ5NzE?platform=server)           |https://api.yunxinapi.com/nimserver/qchat/updateWhiteBlackIdentify.action               
|[ 分页查询频道黑白名单成员列表](https://doc.yunxin.163.com/messaging/docs/TQzNzM2MjA?platform=server)      |https://api.yunxinapi.com/nimserver/qchat/queryWhiteBlackIdentifyUser.action            
|[ 分页查询频道黑白名单身份组列表](https://doc.yunxin.163.com/messaging/docs/TUxNDQ5MjE?platform=server)    |https://api.yunxinapi.com/nimserver/qchat/queryWhiteBlackIdentify.action                
|[ 批量查询频道黑白名单成员 ](https://doc.yunxin.163.com/messaging/docs/zQxNzk0NDc?platform=server)         |https://api.yunxinapi.com/nimserver/qchat/batchGetWhiteBlackIdentifyUser.action         
|[ 批量查询频道黑白名单身份组](https://doc.yunxin.163.com/messaging/docs/Tk3MDQ4Mjk?platform=server)        |https://api.yunxinapi.com/nimserver/qchat/batchGetWhiteBlackIdentify.action             

## 圈组频道分组相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 创建频道分组 ](https://doc.yunxin.163.com/messaging/docs/TIwMjk2NDU?platform=server)                   |https://api.yunxinapi.com/nimserver/qchat/createChannelCategory.action                   
|[ 删除频道分组 ](https://doc.yunxin.163.com/messaging/docs/TIzNTIxMzQ?platform=server)                     |https://api.yunxinapi.com/nimserver/qchat/removeChannelCategory.action                   
|[ 修改频道分组信息  ](https://doc.yunxin.163.com/messaging/docs/Dc2MDQyNjI?platform=server)                |https://api.yunxinapi.com/nimserver/qchat/updateChannelCategory.action                   
|[ 批量查询频道分组信息  ](https://doc.yunxin.163.com/messaging/docs/TgwMDE3ODc?platform=server)                |https://api.yunxinapi.com/nimserver/qchat/getChannelCategorys.action                     
|[ 分页查询服务器下频道分组信息 ](https://doc.yunxin.163.com/messaging/docs/TU5NTM3MTc?platform=server)     |https://api.yunxinapi.com/nimserver/qchat/getChannelCategoryListByServerPage.action      
|[ 分页查询频道分组下的频道信息 ](https://doc.yunxin.163.com/messaging/docs/zE1NzM4NzA?platform=server)     |https://api.yunxinapi.com/nimserver/qchat/getChannelListByChannelCategoryPage.action     
|[ 修改频道分组黑白名单身份组  ](https://doc.yunxin.163.com/messaging/docs/TYwNDgyOTM?platform=server)      |https://api.yunxinapi.com/nimserver/qchat/updateCategoryWhiteBlackIdentify.action        
|[ 修改频道分组黑白名单成员  ](https://doc.yunxin.163.com/messaging/docs/jI2NTczNDY?platform=server)        |https://api.yunxinapi.com/nimserver/qchat/updateCategoryWhiteBlackIdentifyUser.action    
|[ 分页查询频道分组黑白名单身份组 ](https://doc.yunxin.163.com/messaging/docs/TAxMDQ5MDM?platform=server)       |https://api.yunxinapi.com/nimserver/qchat/queryCategoryWhiteBlackIdentifyPage.action     
|[ 查询频道分组黑白名单成员 ](https://doc.yunxin.163.com/messaging/docs/TQxMjEwNDg?platform=server)         |https://api.yunxinapi.com/nimserver/qchat/queryCategoryWhiteBlackIdentifyUserPage.action 
|[ 批量查询频道分组黑白名单身份组 ](https://doc.yunxin.163.com/messaging/docs/zk3NDUxNzg?platform=server)   |https://api.yunxinapi.com/nimserver/qchat/batchGetCategoryWhiteBlackIdentify.action      
|[ 批量查询频道分组黑白名单成员](https://doc.yunxin.163.com/messaging/docs/TU1Njk0MDc?platform=server)      |https://api.yunxinapi.com/nimserver/qchat/batchGetCategoryWhiteBlackIdentifyUser.action  

## 圈组身份组相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 创建服务器身份组 ](https://doc.yunxin.163.com/messaging/docs/DI4NzcyMTc?platform=server)                 |https://api.yunxinapi.com/nimserver/qchat/createServerIdentify.action                   
|[ 修改服务器身份组  ](https://doc.yunxin.163.com/messaging/docs/DI4NzcyMTc?platform=server#修改服务器身份组)                 |https://api.yunxinapi.com/nimserver/qchat/updateServerIdentify.action                   
|[ 删除服务器身份组  ](https://doc.yunxin.163.com/messaging/docs/DI4NzcyMTc?platform=server#删除服务器身份组)                 |https://api.yunxinapi.com/nimserver/qchat/removeServerIdentify.action                   
|[ 批量更新服务器身份组优先级](https://doc.yunxin.163.com/messaging/docs/DI4NzcyMTc?platform=server#批量更新服务器身份组优先级)         |https://api.yunxinapi.com/nimserver/qchat/batchUpdateServerIdentifyPriority.action       
|[ 分页查询服务器身份组](https://doc.yunxin.163.com/messaging/docs/DI4NzcyMTc?platform=server#分页查询服务器身份组)               |https://api.yunxinapi.com/nimserver/qchat/getServerIdentifyPages.action                 
|[ 添加服务器身份组成员](https://doc.yunxin.163.com/messaging/docs/jg5NDM3ODE?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/createServerIdentifyMember.action             
|[ 移除服务器身份组成员 ](https://doc.yunxin.163.com/messaging/docs/jg5NDM3ODE?platform=server#移除服务器身份组成员)              |https://api.yunxinapi.com/nimserver/qchat/deleteServerIdentifyMember.action             
|[ 分页查询服务器身份组成员 ](https://doc.yunxin.163.com/messaging/docs/jg5NDM3ODE?platform=server#分页查询服务器身份组成员)          |https://api.yunxinapi.com/nimserver/qchat/getServerIdentifyMemberPages.action           
|[ 分页查询用户所属的身份组](https://doc.yunxin.163.com/messaging/docs/jg5NDM3ODE?platform=server#分页查询用户所属的身份组)           |https://api.yunxinapi.com/nimserver/qchat/getUserServerIdentify.action                  
|[ 创建频道身份组 ](https://doc.yunxin.163.com/messaging/docs/Dg1NDY3NTU?platform=server)                    |https://api.yunxinapi.com/nimserver/qchat/createChannelIdentify.action                 
|[ 修改频道身份组 ](https://doc.yunxin.163.com/messaging/docs/Dg1NDY3NTU?platform=server#修改频道身份组)                    |https://api.yunxinapi.com/nimserver/qchat/updateChannelIdentify.action                  
|[ 删除频道身份组 ](https://doc.yunxin.163.com/messaging/docs/Dg1NDY3NTU?platform=server#删除频道身份组)                    |https://api.yunxinapi.com/nimserver/qchat/deleteChannelIdentify.action                  
|[ 分页查询频道身份组 ](https://doc.yunxin.163.com/messaging/docs/Dg1NDY3NTU?platform=server#分页查询频道身份组)                |https://api.yunxinapi.com/nimserver/qchat/getChannelIdentifyPages.action                
|[ 创建用户定制权限 ](https://doc.yunxin.163.com/messaging/docs/Tc2MjEzMTk?platform=server)                  |https://api.yunxinapi.com/nimserver/qchat/createUserIdentify.action                     
|[ 删除用户定制权限  ](https://doc.yunxin.163.com/messaging/docs/Tc2MjEzMTk?platform=server#删除用户定制权限)                 |https://api.yunxinapi.com/nimserver/qchat/deleteUserIdentify.action                     
|[ 修改用户定制权限 ](https://doc.yunxin.163.com/messaging/docs/Tc2MjEzMTk?platform=server#%E4%BF%AE%E6%94%B9%E7%94%A8%E6%88%B7%E5%AE%9A%E5%88%B6%E6%9D%83%E9%99%90)                  |https://api.yunxinapi.com/nimserver/qchat/updateUserIdentify.action                    
|[ 分页查询用户定制权限 ](https://doc.yunxin.163.com/messaging/docs/Tc2MjEzMTk?platform=server#修改用户定制权限)              |https://api.yunxinapi.com/nimserver/qchat/getUserIdentifyPages.action                  
|[ 创建频道分组身份组](https://doc.yunxin.163.com/messaging/docs/zQzODk3NjA?platform=server)                 |https://api.yunxinapi.com/nimserver/qchat/createChannelCategoryIdentify.action           
|[ 修改频道分组身份组](https://doc.yunxin.163.com/messaging/docs/zQzODk3NjA?platform=server#修改频道分组身份组)                 |https://api.yunxinapi.com/nimserver/qchat/updateChannelCategoryIdentify.action           
|[ 删除频道分组身份组 ](https://doc.yunxin.163.com/messaging/docs/zQzODk3NjA?platform=server#删除频道分组身份组)                |https://api.yunxinapi.com/nimserver/qchat/deleteChannelCategoryIdentify.action           
|[ 分页查询频道身份组列表 ](https://doc.yunxin.163.com/messaging/docs/zQzODk3NjA?platform=server#分页查询频道分组身份组列表)            |https://api.yunxinapi.com/nimserver/qchat/getChannelCategoryIdentify.action              
|[ 创建频道分组下某人的定制权限](https://doc.yunxin.163.com/messaging/docs/jYyMDU1MTI?platform=server#创建频道分组下某人的定制权限)       |https://api.yunxinapi.com/nimserver/qchat/createChannelCategoryUserIdentify.action       
|[ 删除频道分组下某人的定制权限](https://doc.yunxin.163.com/messaging/docs/jYyMDU1MTI?platform=server#删除频道分组下某人的定制权限)       |https://api.yunxinapi.com/nimserver/qchat/deleteChannelCategoryUserIdentify.action       
|[ 修改频道分组下某人的定制权限](https://doc.yunxin.163.com/messaging/docs/jYyMDU1MTI?platform=server#修改频道分组下某人的定制权限)       |https://api.yunxinapi.com/nimserver/qchat/updateChannelCategoryUserIdentify.action       
|[ 分页查询频道分组下某人的定制权限](https://doc.yunxin.163.com/messaging/docs/jYyMDU1MTI?platform=server#分页查询频道分组下某人的定制权限)   |https://api.yunxinapi.com/nimserver/qchat/getChannelCategoryUserIdentify.action         
|[ 创建自定义权限  ](https://doc.yunxin.163.com/messaging/docs/zk3MzE0MjA?platform=server#创建自定义权限)                   |https://api.yunxinapi.com/nimserver/qchat/createCustomAuth.action                      
|[ 删除自定义权限](https://doc.yunxin.163.com/messaging/docs/zk3MzE0MjA?platform=server#删除自定义权限项)                     |https://api.yunxinapi.com/nimserver/qchat/deleteCustomAuth.action                       
|[ 查询所有自定义权限 ](https://doc.yunxin.163.com/messaging/docs/zk3MzE0MjA?platform=server#查询所有自定义权限)                |https://api.yunxinapi.com/nimserver/qchat/listAllCustomAuth.action                       
|[ 查询自定义权限项列表 ](https://doc.yunxin.163.com/messaging/docs/zk3MzE0MjA?platform=server#查询自定义权限项列表)              |https://api.yunxinapi.com/nimserver/qchat/listCustomAuthByAuthBits.action                
|[ 查询用户拥有的权限 ](https://doc.yunxin.163.com/messaging/docs/TM4MjQ2NTI?platform=server)                |https://api.yunxinapi.com/nimserver/qchat/queryIdentifyResources.action                  


## 圈组消息相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 圈组发送消息](https://doc.yunxin.163.com/messaging/docs/zI5ODE5MzY?platform=server)                     |https://api.yunxinapi.com/nimserver/qchat/sendMsg.action                                
|[ 更新消息  ](https://doc.yunxin.163.com/messaging/docs/zI2MDUzNzk?platform=server)                        |https://api.yunxinapi.com/nimserver/qchat/updateMsg.action                              
|[ 查询云端历史消息 ](https://doc.yunxin.163.com/messaging/docs/zE5NjI2NDM?platform=server)                 |  https://api.yunxinapi.com/nimserver/qchat/queryHistoryMsg.action                       
|[ 查询 Thread 聊天历史 ](https://doc.yunxin.163.com/messaging/docs/jQ2NDMzNzA?platform=server)             |https://api.yunxinapi.com/nimserver/qchat/queryThreadTalkHistory.action                  
|[ 批量查询 Thread 聊天 meta 信息](https://doc.yunxin.163.com/messaging/docs/jk0MjIyMjg?platform=server)    |https://api.yunxinapi.com/nimserver/qchat/batchQueryThreadTalkMeta.action                |
|[ 更新快捷评论       ](https://doc.yunxin.163.com/messaging/docs/DUxNDg0OTA?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/updateQuickComment.action                      |
|[ 查询快捷评论   ](https://doc.yunxin.163.com/messaging/docs/DQ0MTQ0OTE?platform=server)                   |https://api.yunxinapi.com/nimserver/qchat/queryQuickComment.action                       |
|[ 查询@某人的未读消息 ](https://doc.yunxin.163.com/messaging/docs/zYzNTM4MTQ?platform=server)              |https://api.yunxinapi.com/nimserver/qchat/queryChannelUnReadMentionedMsgPage.action      

## 圈组系统通知相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 发送自定义系统通知 ](https://doc.yunxin.163.com/messaging/docs/jQ2MjQwNDg?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/sendAttachMsg.action                         
|[ 更新自定义系统通知 ](https://doc.yunxin.163.com/messaging/docs/jU0ODU4Nzc?platform=server)               |https://api.yunxinapi.com/nimserver/qchat/updateAttachMsg.action                        

## 圈组搜索结果自定义排序相关

| API                                    | 请求URL                                                               |
|----------------------------------------|-----------------------------------------------------------------------|
|[ 修改服务器自定义排序值   ](https://doc.yunxin.163.com/messaging/docs/TExNDI3ODU?platform=server)         |  https://api.yunxinapi.com/nimserver/qchat/batchUpdateServerReorderWeight.action         
|[ 修改频道自定义排序值  ](https://doc.yunxin.163.com/messaging/docs/Tg1NDMyNDk?platform=server)            |https://api.yunxinapi.com/nimserver/qchat/batchUpdateChannelReorderWeight.action         