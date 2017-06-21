# OrderQuery - 订单查询

**应用场景**

根据商户订单号或者平台订单号查询平台的具体订单信息。

###### 

**接口链接**

> [http://{BaseURL}/UnifiedPay/Gateway](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**公共请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| method | 是 | orderquery | 接口名称，orderquery |
| version | 否 | 1.0 | 调用方版本号 |
| pid | 否 | yunpos | 调用方产品名称 |
| sign | 是 | 00000000000000000000000000000000 | 请求参数的签名串 |

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| paytype | 是 | WECHAT | 支付方式，详见参数规定 |
| mch\_id | 是 | 00000001 | 超赢商户号 |
| out\_trade\_no | 否 | 1497769914931 | 商户系统内部的订单号，out\_trade\_no和transaction\_id至少一个必填，同时存在时transaction\_id优先 |
| transaction\_id | 否 | 7551000001201706166172780576 | 平台交易号，out\_trade\_no和transaction\_id至少一个必填，同时存在时transaction\_id优先。 |

**请求参数示例**

> method=orderquery&paytype=WECHAT&mch\_id=00000001&out\_trade\_no=1497769914931&sign=00000000000000000000000000000000

**响应结果**

| 字段名 | 必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| state | 是 | String | 通讯状态，详见参数规定 |
| code | 是 | String | 状态码 ，详见参数规定 |
| msg | 否 | String | 返回信息 |
| trade\_state | 否 | String | 交易状态，详见参数规定 |
| sign | 是 | String | 响应结果的签名串 |

以下字段在state和trade\_state都为SUCCESS的时候有返回

| 字段名 | 必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| mch\_id | 是 | String | 超赢商户号 |
| appid | 是 | String | 调用接口提交的公众账号ID |
| is\_subscribe | 是 | String | 用户是否关注公众账号，仅在公众账号类型支付有效，取值范围：Y或N;Y-关注;N-未关注 |
| openid | 是 | String | 用户在商户 appid 下的唯一标识 |
| sub\_appid | 是 | String | 调用接口提交的子商户公众账号ID |
| sub\_is\_subscribe | 是 | String | 用户是否关注子公众账号，仅在公众账号类型支付有效，取值范围：Y或N;Y-关注;N-未关注 |
| sub\_openid | 是 | String | 子商户appid下用户唯一标识，如需返回则请求时需要传sub\_appid |
| transaction\_id | 是 | String | 平台交易号 |
| out\_transaction\_id | 是 | String | 第三方订单号 |
| out\_trade\_no | 是 | String | 商户系统内部的定单号，32个字符内、可包含字母 |
| total\_fee | 是 | String | 总金额，以分为单位，只能为整数 |
| coupon\_fee | 否 | String | 代金券金额，代金券金额&lt;=订单金额，订单金额 - 代金券金额 = 现金支付金额 |
| fee\_type | 否 | String | 货币类型，符合 ISO 4217 标准的三位字母代码，默认人民币：CNY |
| attach | 否 | String | 商家数据包，原样返回 |
| bank\_type | 否 | String | 付款银行 |
| bank\_billno | 否 | String | 银行订单号，若为第三方支付则为空 |
| time\_end | 是 | String | 支付完成时间，格式为yyyyMMddHHmmss，如2009年12月25日9点10分10秒表示为20091225091010。时区为GMT+8 Beijing |
| nonce\_str | 是 | String | 随机字符串 |

**响应结果示例**

```js
{
    "state": "SUCCESS",
    "code": "10000",
    "trade_state": "SUCCESS",
    "msg": "SUCCESS",
    "mch_id": "WFT01",
    "appid": "wx1f87d44db95cba7a",
    "is_subscribe": "N",
    "openid": "oywgtuCJFeGzT-QtF-8U7FHb1z3Q",
    "sub_appid": "wxce38685bc050ef82",
    "sub_is_subscribe": "N",
    "sub_openid": "oHmbktxFlpoEPo2Ol5GOJniV2q-A",
    "transaction_id": "7551000001201706196281085687",
    "out_transaction_id": "4005572001201706196460269701",
    "out_trade_no": "1497862554883",
    "total_fee": "1",
    "fee_type": "CNY",
    "bank_type": "CFT",
    "time_end": "20170619165616",
    "nonce_str": "a849df6660cb4354b6fe5b23120a73ce",
    "sign": "D292DB710872C023A9A1CF429457E0B3"
}
```



