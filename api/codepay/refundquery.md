# RefundQuery - 退款查询

**应用场景**

提交退款申请后， 通过调用该接口查询退款状态。 银行卡支付的退款有一定延时， 请在 3 个工作日后重新查询退款状态。

**注意**

1. 如果单个支付订单部分退款次数超过20次请使用平台退款单号查询
2. 若存在多条退款单时，退款状态请以refund\_list中refund\_status字段为准

**校验签名**

> 是

**接口链接**

> [http://{BaseURL}/UnifiedPay/Gateway](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**公共请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| method | 是 | refundquery | 接口名称，refundquery |
| agent\_id | 是 | 13000000000000001 | 代理商编号 |
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

> method=refundquery&paytype=WECHAT&mch\_id=00000001&out\_trade\_no=1497769914931&sign=00000000000000000000000000000000

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
| appid | 否 | 调用接口提交的公众账号ID |
| is\_subscribe | 否 | 用户是否关注公众账号，仅在公众账号类型支付有效，取值范围：Y或N;Y-关注;N-未关注 |
| openid | 否 | 用户在商户 appid 下的唯一标识 |
| sub\_appid | 否 | 调用接口提交的子商户公众账号ID |
| sub\_is\_subscribe | 否 | 用户是否关注子公众账号，仅在公众账号类型支付有效，取值范围：Y或N;Y-关注;N-未关注 |
| sub\_openid | 否 | 子商户appid下用户唯一标识，如需返回则请求时需要传sub\_appid |
| transaction\_id | 是 | 平台交易号 |
| out\_transaction\_id | 是 | 第三方订单号 |
| out\_trade\_no | 是 | 商户系统内部的定单号，32个字符内、可包含字母 |
| refund\_count | 是 | 退款笔数 |
| refund\_fee\_summary | 是 | 退款汇总金额，以分为单位，只能为整数 |
| refund\_list | 是 | 退款单集合 |
| nonce\_str | 是 | 随机字符串 |

以下字段在refund\_list中返回

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| serial\_no | 是 | 退款序号，按退款申请时间升序排列 |
| refund\_id | 是 | 平台退款单号 |
| out\_refund\_id | 是 | 第三方退款单号 |
| out\_refund\_no | 是 | 商户退款单号 |
| refund\_channel | 否 | 退款渠道，ORIGINAL—原路退款，默认 |
| refund\_fee | 是 | 当次退款金额，以分为单位，只能为整数 |
| refund\_status | 是 | 退款状态：SUCCESS—退款成功；FAIL—退款失败；PROCESSING—退款处理中；NOTSURE—未确定， 需要商户原退款单号重新发起；CHANGE—转入代发，退款到银行发现用户的卡作废或者冻结了，导致原路退款银行卡失败，资金回流到商户的现金帐号，需要商户人工干预，通过线下或者平台转账的方式进行退款。 |
| refund\_time | 否 | 退款时间，格式为yyyyMMddHHmmss，如2009年12月25日9点10分10秒表示为20091225091010。时区为GMT+8 Beijing |
| coupon\_refund\_fee | 否 | 现金券退款金额 &lt;= 退款金额， 退款金额 - 现金券退款金额为现金 |

**响应结果示例**

```js
{
    "state": "SUCCESS",
    "code": "10000",
    "trade_state": "SUCCESS",
    "msg": "SUCCESS",
    "mch_id": "00000001",
    "appid": "wxe00fda5293a2fa25",
    "transaction_id": "199520175115201706224112697859",
    "out_transaction_id": "4005572001201706226919222698",
    "out_trade_no": "1498125915060",
    "refund_list": "[{\"serial_no\":\"0\",\"refund_id\":\"199520175115201706224212715917\",\"out_refund_id\":\"50000203302017062201274913961\",\"out_refund_no\":\"TK-1498125915060-0.02\",\"refund_channel\":\"ORIGINAL\",\"refund_fee\":\"2\",\"refund_status\":\"SUCCESS\",\"refund_time\":\"20170622182219\"},{\"serial_no\":\"1\",\"refund_id\":\"199520175115201706226290021966\",\"out_refund_id\":\"50000203302017062201275383549\",\"out_refund_no\":\"TK-1498125915060-0.01-1\",\"refund_channel\":\"ORIGINAL\",\"refund_fee\":\"1\",\"refund_status\":\"SUCCESS\",\"refund_time\":\"20170622181822\"}]",
    "refund_fee_summary": "3",
    "refund_count": "2",
    "nonce_str": "65f753cf49f049c4ab434a7caa75449c",
    "sign": "0FB65206D136E3A09D63B905F91D3B6B"
}
```



