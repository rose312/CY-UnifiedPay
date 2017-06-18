# 协议规则

| 规则 | 描述 |
| :--- | :--- |
| 传输方式 | 为保证交易安全性，采用HTTPS传输（开发时可使用HTTP） |
| 数据格式 | 提交和返回数据都为JSON格式（application/json） |
| 字符编码 | 统一采用UTF-8字符编码 |
| 内容类型 | 统一采用x-www-form-urlencoded编码格式 |
| 签名算法 | MD5，后续会兼容SHA1、SHA256、HMAC等 |
| 签名要求 | 部份接口需要校验签名 |

# 签名验证

签名生成的通用步骤如下：

第一步，设所有传输的数据为集合M，将集合M内非空参数值的参数按照参数名ASCII码从小到大排序（字典序），使用URL键值对的格式（即key1=value1&key2=value2…）拼接成字符串stringA。

特别注意以下重要规则：

* 参数名ASCII码从小到大排序（字典序）；
* 如果参数的值为空不参与签名；
* 参数名区分大小写；
* 验证调用返回或主动通知签名时，传送的sign参数不参与签名，将生成的签名与该sign值作校验。
* 接口可能增加字段，验证签名时必须支持增加的扩展字段

第二步，在stringA最后拼接上key得到stringSignTemp字符串（即stringA&key={KEY}），并对stringSignTemp进行MD5运算，再将得到的字符串所有字符转换为大写，得到sign值signValue。

# 请求格式

###### 请求示例

> Javascript

```js
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://{BaseURL}/OpenPlatform/GetUserInfo",
  "method": "POST",
  "headers": {
    "content-type": "application/x-www-form-urlencoded",
    "cache-control": "no-cache",
    "X-Requested-With":"XMLHttpRequest",
  },
  "data": {
    "token": "00000000-0000-0000-0000-000000000000"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Python

```py
import requests

url = "http://{BaseURL}/OpenPlatform/GetUserInfo"

payload = "token=00000000-0000-0000-0000-000000000000"
headers = {
    'content-type': "application/x-www-form-urlencoded",
    'cache-control': "no-cache",
    'X-Requested-With': "XMLHttpRequest",
    }

response = requests.request("POST", url, data=payload, headers=headers)
print(response.text)
```

# 响应格式

| 字段名 | 必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| code | 是 | String | 状态码，10000-成功，10001-错误，10002-令牌无效 |
| msg | 是 | String | 返回信息，若调用失败则为错误原因 |
| data | 否 | String | 当调用成功且接口有具体数据响应，则有返回。 |

###### 成功示例

```js
{
    "code": "10000",
    "msg": "Success",
    "data": "{\"Name\":\"姓名\",\"CompanyName\":\"公司名称\",\"ID\":3308444987384064,\"Phone\":\"13800138000\"}"
}
```

###### 失败示例

```js
{
    "code": "10001",
    "msg": "用户未登录"
}
```



