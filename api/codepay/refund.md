# Refund - 交易退款

**应用场景**

商户针对某一个已经成功支付的订单发起退款，操作结果在同一会话中同步返回。

**退款方式**

目前只支持原路返回退款

说明：退到银行卡则是非实时的，每个银行的处理速度不同，一般发起退款后1-3个工作日内到账。

同一笔单的部分退款需要设置相同的订单号和不同的 out\_refund\_no 。一笔退款失败后重新提交，要采用原来 的out\_refund\_no。总退款金额不能超过用户实际支付金额\(现金券金额不能退款\)

**退款限制**

商户在退款操作时应该注意退款限制，避免发起不会成功的退款请求，下面是主要的退款限制：

1.在平台系统中，只要退款累计金额不超过交易单支付总额，一笔交易单可以多次退款，退款申请单号（退款接口中有此参数）唯一确定一次退款，而      不是交易单号确定一次退款。退款申请单号由商户生成，所以商户一定要保证退款申请单的唯一性。商家在退款过程中要特别注意，只有在能确定退      款失败的情况下，才能重新发起另一笔退款。

2.目前大多数银行都支持全额退款和部分退款，但是也有少数银行不支持全额退款或部分退款，或者不支持退款。在这种情况下，商户可以与买家协调，    线下直接退款给买家。

**接口链接**

> [http://{BaseURL}/UnifiedPay/Gateway](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**公共请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| method | 是 | refund | 接口名称，refund |
| version | 否 | 1.0 | 调用方版本号 |
| pid | 否 | yunpos | 调用方产品名称 |
| sign | 是 | 00000000000000000000000000000000 | 请求参数的签名串 |

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| paytype | 是 | WECHAT | 支付方式，详见参数规定 |
| mch\_id | 是 | 00000001 | 超赢商户号 |
| out\_trade\_no | 否 | 1497769914931 | 商户系统内部的订单号，out\_trade\_no和transaction\_id至少一个必填，同时存在时transaction\_id优先 |
| transaction\_id | 否 | 7551000001201706166172780576 | 平台单号, out\_trade\_no和transaction\_id至少一个必填，同时存在时transaction\_id优先 |
| out\_refund\_no | 是 | TK-1497769914931-01 | 商户退款单号，32个字符内、可包含字母，确保在商户系统唯一。同个退款单号多次请求，平台当一个单处理，只会退一次款。如果出现退款不成功，请采用原退款单号重新发起，避免出现重复退款。 |
| total\_fee | 是 | 1 | 订单总金额，单位为分 |
| refund\_fee | 是 | 1 | 退款金额，单位为分，可以做部分退款 |
| op\_user\_id | 是 | 00000001 | 操作员帐号，默认为商户号 |

**请求参数示例**

> method=refund&paytype=WECHAT&mch\_id=00000001&out\_trade\_no=1497769914931&out\_refund\_no=TK-1497769914931-01&sign=00000000000000000000000000000000

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
| transaction\_id | 是 | String | 平台交易号 |
| out\_trade\_no | 是 | String | 商户系统内部的定单号，32个字符内、可包含字母 |
| out\_refund\_no | 是 | String | 商户退款单号 |
| refund\_id | 是 | String | 平台退款单号 |
| refund\_channel | 否 | String | 退款渠道，ORIGINAL—原路退款，默认 |
| refund\_fee | 是 | String | 退款总金额，单位为分，可以做部分退款 |
| coupon\_refund\_fee | 是 | String | 现金券退款金额 &lt;= 退款金额， 退款金额-现金券退款金额为现金 |
| nonce\_str | 是 | String | 随机字符串 |

**响应结果示例**

```js
{
    "code": "10000",
    "state": "0",
    "msg": "Success",
    "trade_state": "wechat",
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
    "sign": "FA3DBE500AA82B944489AC18B53B2DAA"
}
```



