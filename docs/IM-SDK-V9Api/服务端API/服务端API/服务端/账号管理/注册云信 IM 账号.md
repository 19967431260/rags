<!--keywords: 注册账号,云信IM账号,IM账号,账号集成,云信账号,账号管理,IM账号管理 -->

登录 IM 前，需注册云信 IM 账号。

本文介绍如何通过云信服务端 API 创建 IM 账号，以及相关的常见问题。

## <span id='功能描述'>功能描述</span>  

该接口用于将当前应用自身账号导入云信 IM 系统，为其创建一个对应的云信系统内部 ID（以下称 **accid** ），使得该账号可使用 IM 功能。

一种典型的账号注册与初次登录的流程如下：

![](https://yx-web-nosdn.netease.im/quickhtml%2Fassets%2Fyunxin%2Fdoc%2FIM-AccountManagement1.png)


上图中，**IM SDK** 集成在应用客户端；**Your App Server** 为您的应用服务器；**IM Server** 为云信服务器。


::: note important 
- 通过服务端 API 创建的账号不会在控制台显示，因此注册成功后，请务必记录云信将返回 accid 与 token ，在开发者自身的应用服务器上维护好 accid 与 token 信息列表。
- 通过服务端 API 创建账号时，云信服务端会对 accid 做小写转换，请注意以 API 返回的accid 为准，以免登录失败。
- token 如果没有更新，将永久有效。
- 点播终端用户的 accid 和 IM 的 accid 是不同的。如果同时使用点播相关功能和 IM 功能，需要分别创建并保存点播终端用户的 accid 和 IM 的 accid，例如分别保存为 vodAccid 和 imAccid。
:::

## API 使用限制

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging/server-apis/zk4Mzg0MjE?platform=server)。

## <span id='URL'>URL</span>

```
POST https://api.yunxinapi.com/nimserver/user/create.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

## <span id='请求参数'>请求参数</span>

- POST 请求中 Headers 的设置请参考[API调用方式](https://doc.yunxin.163.com/messaging/docs/jk3MzY2MTI?platform=server)。

- POST 请求中 Body 的设置如下：

<table>
<tr>
<td width=15%><b>参数名称</b></td>
<td width=15%><b>类型</b></td>
<td width=15%><b>字符串长度上限</b></td>
<td width=10%><b>是否必选</b></td>
<td width=20%><b>示例</b></td>
<td width=25%><b>描述</b></td>
</tr>
<tr>
<td>accid</td>
<td>String</td>
<td>32</td>
<td>必选</td>
<td>"123456"</td>
<td>云信 IM 账号，必须保证唯一性。若涉及字母，传参时请一律小写处理。只允许字母、数字、半角下划线_、@、半角点以及半角-。请注意以此接口返回结果中的accid为准。</td>
</tr>
<tr>
<td>token</td>
<td>String</td>
<td>128</td>
<td>选填</td>
<td>"abcdef"</td>
<td>用户账号对应的登录密钥token。如果未指定，云信会自动生成token，并在创建成功后返回。</td>
</tr>
<tr>
<td>name</td>
<td>String</td>
<td>64</td>
<td>选填</td>
<td>"zhangsan"</td>
<td>用户昵称</td>
</tr>
<tr>
<td>icon</td>
<td>String</td>
<td>1024</td>
<td>选填</td>
<td>"https://netease/xxx.png"</td>
<td>用户头像 URL</td>
</tr>
<tr>
<td>sign</td>
<td>String</td>
<td>256</td>
<td>选填</td>
<td>"Hello World"</td>
<td>用户签名</td>
</tr>
<tr>
<td>email</td>
<td>String</td>
<td>64</td>
<td>选填</td>
<td>"xxx@163.com"</td>
<td>用户邮箱地址</td>
</tr>
<tr>
<td>birth</td>
<td>String</td>
<td>16</td>
<td>选填</td>
<td>"xxxx-xx-xx"</td>
<td>用户生日</td>
</tr>
<tr>
<td>mobile</td>
<td>String</td>
<td>32</td>
<td>选填</td>
<td>"+852-xxxxxxxx"</td>
<td>用户手机号码，非中国大陆手机号码需要填写国家代码(如美国：+1-xxxxxxxxxx)或地区代码(如香港：+852-xxxxxxxx)</td>
</tr>
<tr>
<td>gender</td>
<td>int</td>
<td>/</td>
<td>选填</td>
<td>2</td>
<td>用户性别，0-未知，1-男，2-女。其它会报参数错误。</td>
</tr>
<tr>
<td>ex</td>
<td>String</td>
<td>1024</td>
<td>选填</td>
<td>{"level":1}</td>
<td>用户资料扩展字段，建议封装成JSON。</td>
</tr>
</table>


## <span id='返回参数'>返回参数</span>

<table>
<tr>
<td width=13%><b>参数名称</b></td>
<td width=13%><b>类型</b></td>
<td width=43%><b>示例</b></td>
<td width=40%><b>描述</b></td>
</tr>
<tr>
<td>code</td>
<td>int</td>
<td>200</td>
<td>状态码</td>
</tr>
<tr>
<td>info</td>
<td>String</td>
<td>{<br/>
      "name": "zhangsan",<br/>
     "accid": "123456",<br/>
     "token": "abcdef"<br/>
    }</td>
<td>注册成功时返回的信息</td>
</tr>
<tr>
<td>desc</td>
<td>String</td>
<td>"already register"</td>
<td>注册失败时返回的信息</td>
</tr>
</table>

## <span id='示例'>示例</span>

### **<span id='请求示例（curl）'>请求示例（curl）</span>**

```curl
curl -X POST -H "AppKey: go9***3mgq3" -H "Nonce: 4t***23t23t" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b***583f86" -H "Content-Type: application/x-www-form-urlencoded" -d 'accid=123456&name=zhangsan' 'https://api.yunxinapi.com/nimserver/user/create.action'
```


### **<span id='注册成功返回示例'>注册成功返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 200,
    "info": {
        "name": "zhangsan",
        "accid": "123456",
        "token": "abcdef"
    }
}
```

### **<span id='注册失败返回示例'>注册失败返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 414,
    "desc": "already register"
}
```

## <span id='状态码'>状态码</span>

该 API 在 HTTPS Body 中返回请求的状态码，状态码详情请参见[状态码](https://doc.yunxin.163.com/messaging/server-apis/TM5NTk2Mzc?platform=server)。



## 常见问题

### 已有大量用户账号的应用，如何进行账号集成？


对于已经存在大量用户帐号的应用，如果需要接入网易云信 IM 服务，我们推荐遵从**按需创建**的原则。

考虑到存量帐号中可能存在相当比例的僵尸用户或非活跃用户，在迁入网易云信时直接全量导入对您是一种不必须要的开销。您可以在用户第一次触发使用网易云信的 IM 行为时检查该用户的是否已创建 IM 账号（`accid`），如未创建则通过后台自动创建再登录，这种方式会使您的用户只有在必要的时候才创建云信的 IM 帐号，同时在云信中创建的用户都是有效的活跃用户。

### 为什么不能通过客户端 SDK 创建账号，必须要通过服务端创建？

网易云信的账号体系和应用的账号体系是业务绑定的关系，通过应用服务端才能创建云信 IM 账号可以有效控制账号的创建行为，任何应用的客户端都存在被破解的风险，如果直接通过客户端就可以创建云信 IM 账号可能会使您的应用出现被盗刷账号的情况（可能友商提供类似的客户端接口，使您在开发时节省了几行代码，但是为您的应用安全埋下了风险的种子）。


### 通过云信服务端 API 注册的 IM 账号可否在云信控制台中查看？

通过云信服务端注册的帐号不会出现在控制台。

这么做的原因是：
- 控制台提供的用户列表只是部分用户列表，是为了方便您在接入云信 IM 服务的过程中，在没有服务端开发的情况下快速进行客户端集成的调试。您可以在控制台上快速的创建测试账号，并在客户端上登录测试；
- 通过云信服务端 API 创建的账号在控制台不显示，是为了保护用户的隐私及帐号安全，以免出现误操作，例如对用户进行不当的禁用或其他操作。


### 注册账号后如何查询/更新姓名等用户信息？

可以通过调用[用户名片](https://doc.yunxin.163.com/messaging/docs/zI0NzYyMDQ?platform=server)相关接口进行查询或更新用户信息，包括用户昵称、年龄、性别等信息。