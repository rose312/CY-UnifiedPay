# Pay - 提交支付

**应用场景**

收银员使用扫码设备读取微信（或支付宝等电子钱包）用户刷卡授权码以后，调用该接口发起支付对用户进行收款。

###### 

**接口链接**

> [http://{BaseURL}/UnifiedPay/Gateway](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**公共请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| method | 是 | pay | 接口名称，pay |
| agent\_id | 是 | 13000000000000001 | 代理商编号 |
| version | 否 | 1.0 | 调用方版本号 |
| pid | 否 | yunpos | 调用方产品名称 |
| sign | 是 | 00000000000000000000000000000000 | 请求参数的签名串 |

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| paytype | 是 | WECHAT | 支付方式，详见参数规定 |
| mch\_id | 是 | 00000001 | 超赢商户号 |
| out\_trade\_no | 是 | 1497769914931 | 商户系统内部的订单号 ,5到32个字符、 只能包含字母数字或者下划线，区分大小写，确保在商户系统唯一 |
| device\_info | 否 | 013467007045764 | 终端设备号，商户自定义。特别说明：对于QQ钱包支付，此参数必传，否则会报错。 |
| body | 是 | image形象店-深圳腾大- QQ公仔 | 商品描述 |
| attach | 否 | 说明 | 商户附加信息，可做扩展参数 |
| total\_fee | 是 | 1 | 总金额，以分为单位，只能为整数 |
| mch\_create\_ip | 否 | 114.114.114.114 | 调用支付API的机器IP |
| auth\_code | 是 | 120061098828009406 | 扫码支付授权码， 设备读取用户展示的条码信息 |
| op\_user\_id | 否 | 00000001 | 操作员帐号，默认为商户号 |
| op\_shop\_id | 否 | md\_001 | 门店编号 |
| op\_device\_id | 否 | device\_01 | 设备编号 |
| goods\_tag | 否 | hot | 商品标记 |

**请求参数示例**

> method=pay&mch\_id=00000001&version=1.0&pid=yunpos&paytype=WECHAT&out\_trade\_no=1497769914931&auth\_code=123123123&body=%E8%B6%85%E8%B5%A2%E6%94%AF%E4%BB%98&total\_fee=1&sign=00000000000000000000000000000000

**响应结果**

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| state | 是 | 通讯状态，详见参数规定 |
| code | 是 | 状态码 ，详见参数规定 |
| msg | 否 | 返回信息 |
| trade\_state | 否 | 交易状态，详见参数规定 |
| sign | 是 | 响应结果的签名串 |

以下字段在state和trade\_state都为SUCCESS的时候有返回

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| mch\_id | 是 | 超赢商户号 |
| appid | 是 | 调用接口提交的公众账号ID |
| is\_subscribe | 是 | 用户是否关注公众账号，仅在公众账号类型支付有效，取值范围：Y或N；Y-关注；N-未关注 |
| openid | 是 | 用户在商户 appid 下的唯一标识 |
| sub\_appid | 是 | 调用接口提交的子商户公众账号ID |
| sub\_is\_subscribe | 是 | 用户是否关注子公众账号，仅在公众账号类型支付有效，取值范围：Y或N;Y-关注;N-未关注 |
| sub\_openid | 是 | 子商户appid下用户唯一标识，如需返回则请求时需要传sub\_appid |
| transaction\_id | 是 | 平台交易号 |
| out\_transaction\_id | 是 | 第三方订单号 |
| out\_trade\_no | 是 | 商户系统内部的定单号，32个字符内、可包含字母 |
| total\_fee | 是 | 总金额，以分为单位，只能为整数 |
| coupon\_fee | 否 | 代金券金额，代金券金额&lt;=订单金额，订单金额 - 代金券金额 = 现金支付金额 |
| fee\_type | 否 | 货币类型，符合 ISO 4217 标准的三位字母代码，默认人民币：CNY |
| attach | 否 | 商家数据包，原样返回 |
| bank\_type | 否 | 付款银行 |
| bank\_billno | 否 | 银行订单号，若为第三方支付则为空 |
| time\_end | 是 | 支付完成时间，格式为yyyyMMddHHmmss，如2009年12月25日9点10分10秒表示为20091225091010。时区为GMT+8 Beijing |
| nonce\_str | 是 | 随机字符串 |

**响应结果示例**

```js
{
    "state": "SUCCESS",
    "code": "10000",
    "trade_state": "SUCCESS",
    "msg": "SUCCESS",
    "mch_id": "00000001",
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



