# RefundQuery - 退款查询

**应用场景**

提交退款申请后， 通过调用该接口查询退款状态。 银行卡支付的退款有一定延时， 请在 3 个工作日后重新查询退款状态。

注意：如果单个支付订单部分退款次数超过20次请使用平台退款单号查询

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
| out\_refund\_no | 否 | TK-1497769914931-01 | 商户退款单号，32个字符内、可包含字母,确保在商户系统唯一。 |
| refund\_id | 否 | 7551000001201706215157548269 | 平台退款单号关于refund\_id、out\_refund\_no、out\_trade\_no 、transaction\_id 四个参数必填一个， 如果同时存在优先级为：refund\_id &gt; out\_refund\_no &gt; transaction\_id &gt; out\_trade\_no；特殊说明：如果是支付宝，refund\_id、out\_refund\_no必填其中一个。 |

**请求参数示例**

> method=refundquery&paytype=WECHAT&mch\_id=00000001&refund\_id=7551000001201706215157548269&sign=00000000000000000000000000000000

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
| transaction\_id | 是 | String | 平台交易号 |
| out\_transaction\_id | 是 | String | 第三方订单号 |
| out\_trade\_no | 是 | String | 商户系统内部的定单号，32个字符内、可包含字母 |
| refund\_count | 是 | String | 退款笔数 |
| - | - | - | - |
| - | - | - | - |
| out\_refund\_id\_$n | 是 | String | 商户退款单ID |
| out\_refund\_no\_$n | 是 | String | 商户退款单号 |
| refund\_id\_$n | 是 | String | 平台退款单号 |
| refund\_channel\_$n | 否 | String | 退款渠道，ORIGINAL—原路退款，默认 |
| refund\_fee\_$n | 是 | String | 总金额，以分为单位，只能为整数 |
| coupon\_refund\_fee\_$n | 否 | String | 现金券退款金额 &lt;= 退款金额， 退款金额-现金券退款金额为现金 |
| refund\_time\_$n | 否 | String | 退款时间，格式为yyyyMMddHHmmss，如2009年12月25日9点10分10秒表示为20091225091010。时区为GMT+8 Beijing |
| refund\_status\_$n | 是 | String | 退款状态：SUCCESS—退款成功FAIL—退款失败PROCESSING—退款处理中NOTSURE—未确定， 需要商户原退款单号重新发起CHANGE—转入代发，退款到银行发现用户的卡作废或者冻结了，导致原路退款银行卡失败，资金回流到商户的现金帐号，需要商户人工干预，通过线下或者平台转账的方式进行退款。 |
| - | - | - | - |
| - | - | - | - |
| nonce\_str | 是 | String | 随机字符串 |

> _$n 表示记录的序号，取值为 0~\($ refund\_count -1\)，例如 refund\_count 指示返回的退款记录有 2 条。第一条序号为“0”，第二条序号为“1”。_

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



