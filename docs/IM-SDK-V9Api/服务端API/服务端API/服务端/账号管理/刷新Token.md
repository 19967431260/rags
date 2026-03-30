<!--keywords: token,Token,刷新token,刷新Token,云信账号,账号管理,IM账号管理 -->



网易云信 IM 服务端支持两种刷新 Token 的方式，即指定 Token 刷新和不指定随机刷新。如果需要主动更新 Token，或者 Token 不慎泄露需要修改 Token，可调用如下两个 API 进行更新。

## <span id='指定token'>指定Token</span>  

### **<span id='功能描述'>功能描述</span>**

通过该接口可以将用户账号更新到指定的token。更新后，需要同时更新自身服务器上维护的Token，此外也要确保客户端再次登录时携带的Token是最新的。

### **API 使用限制**

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging/server-apis/zk4Mzg0MjE?platform=server)。

### **<span id='URL'>URL</span>**

```http
POST https://api.yunxinapi.com/nimserver/user/update.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### **<span id='请求参数'>请求参数</span>**

- POST 请求中 Headers 的设置请参考[API调用方式](/docs/TM5MzM5Njk/jk3MzY2MTI)。

- POST 请求中 Body 的设置如下：

<table>
<tr>
<td width=10%><b>参数名称</b></td>
<td width=10%><b>类型</b></td>
<td width=16%><b>字符串长度上限</b></td>
<td width=13%><b>是否必选</b></td>
<td width=16%><b>示例</b></td>
<td width=30%><b>描述</b></td>
</tr>
<tr>
<td>accid</td>
<td>String</td>
<td>32</td>
<td>必选</td>
<td>"123456"</td>
<td>待刷新的云信账号</td>
</tr>
<tr>
<td>props</td>
<td>String</td>
<td>1024</td>
<td>选填</td>
<td>{"k":"v"}</td>
<td>该参数已不建议使用。</td></tr>
</tr>
</tr>
<td>token</td>
<td>String</td>
<td>128</td>
<td>选填</td>
<td>"abcdef"</td>
<td>新的token</td>
</tr>
</table>


### **<span id='示例'>示例</span>**
#### **<span id='请求示例（curl）'>请求示例（curl）</span>**

```curl
curl -X POST -H "AppKey: go9dnk4***9jd9vmel1kglw0803mgq3" -H "Nonce: 4tgggergigw***3t23t" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962cf***f7316fcc55583f86" -H "Content-Type: application/x-www-form-urlencoded" -d 'accid=zhangsan&token=123456' 'https://api.yunxinapi.com/nimserver/user/update.action'
```

#### **<span id='刷新成功返回示例'>刷新成功返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 200
}
```

#### **<span id='刷新失败返回示例'>刷新失败返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 414,
    "desc": "zhangsan not register"
}
```


## <span id='不指定token'>不指定Token</span>

### **<span id='功能描述'>功能描述</span>**

通过该接口可以将用户账号更新到由云信服务器随机生成的token。更新后，需要同时更新自身服务器上维护的token，此外也要确保客户端再次登录时携带的token是最新的。

### **API 使用限制**

单个应用默认最高调用频率请参考 [频控说明](https://doc.yunxin.163.com/messaging/server-apis/zk4Mzg0MjE?platform=server)。

### **<span id='URL'>URL</span>**

```http
POST https://api.yunxinapi.com/nimserver/user/refreshToken.action HTTP/1.1
Content-Type:application/x-www-form-urlencoded;charset=utf-8
```

### **<span id='请求参数'>请求参数</span>**

- POST 请求中 Headers 的设置请参考[API调用方式](/docs/TM5MzM5Njk/jk3MzY2MTI)。

- POST 请求中 Body 的设置如下：


<table>
<tr>
<td width=10%><b>参数名称</b></td>
<td width=10%><b>类型</b></td>
<td width=16%><b>字符串长度上限</b></td>
<td width=13%><b>是否必选</b></td>
<td width=13%><b>示例</b></td>
<td width=30%><b>描述</b></td>
</tr>
<tr>
<td>accid</td>
<td>String</td>
<td>32</td>
<td>必选</td>
<td>"123456"</td>
<td>待刷新的云信账号</td>
</tr>
</table>

### **<span id='示例'>示例</span>**
#### **<span id='请求示例（curl）'>请求示例（curl）</span>**

```curl
curl -X POST -H "AppKey: go9dnk49bkd9jd9v***1kglw0803mgq3" -H "Nonce: 4tgggergig***323t23t" -H "CurTime: 1443592222" -H "CheckSum: 9e9db3b6c9abb2e1962c***6f7316fcc55583f86" -H "Content-Type: application/x-www-form-urlencoded" -d 'accid=zhangsan' 'https://api.yunxinapi.com/nimserver/user/refreshToken.action'
```

#### **<span id='刷新成功返回示例'>刷新成功返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 200,
    "info": {
        "accid": "zhangsan",
        "token": "07b9ee85767990779707af4030******"
    }
}
```

#### **<span id='刷新失败返回示例'>刷新失败返回示例</span>**

```json
"Content-Type": "application/json; charset=utf-8"
{
    "code": 414,
    "desc": "zhangsan not register"
}
```


## <span id='状态码'>状态码</span>

该接口在 HTTPS Body 中返回请求的状态码，状态码列表请参考[状态码](https://doc.yunxin.163.com/messaging/server-apis/TM5NTk2Mzc?platform=server)。