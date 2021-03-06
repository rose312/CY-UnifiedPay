# Mch\_Reg - 注册超赢虚拟商户

**应用场景**

该接口提供第三方接入使用我方聚合支付业务时注册成超赢虚拟商户功能。

**校验签名**

> 是

**接口链接**

> http://{BaseURL}/UnifiedPay/Mch\_Reg

**提交方式**

> POST

**公共请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| agent\_id | 是 | 13000000000000001 | 代理商编号 |
| version | 否 | 1.0 | 调用方版本号 |
| pid | 否 | yunpos | 调用方产品名称 |
| sign | 是 | 00000000000000000000000000000000 | 请求参数的签名串 |

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| - | 是 | - | 具体参数，联调时请联系技术支持获取 |

**请求参数示例**

> key1=aaa&key2=bbb&sign=00000000000000000000000000000000

**响应结果**

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| state | 是 | 通讯状态，详见参数规定 |
| code | 是 | 状态码 ，详见参数规定 |
| msg | 否 | 返回信息 |
| sign | 是 | 响应结果的签名串 |

以下字段在state为SUCCESS，code为10000的时候有返回

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| mch\_id | 是 | 超赢商户号 |

**响应结果示例**

```js
{
    "state": "SUCCESS",
    "code": "10000",
    "msg": "SUCCESS",
    "mch_id": "00000001",
    "nonce_str": "f1625e94362d4d82aafcc5fc9d1f9325",
    "sign": "00000000000000000000000000000000"
}
```



