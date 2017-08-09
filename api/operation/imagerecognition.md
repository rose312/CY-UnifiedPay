# ImageRecognition - 图像识别

**应用场景**

该接口提供现有图像识别，并返回图片内容。

**校验签名**

> 否

**接口链接**

> [http://{BaseURL}/Utility/ImageRecognition](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| img\_url | 是 | /UpLoad/Temp/597e64e68d264273a4e23e477d472c5b.jpg | jpg格式图片，进行base64编码，去掉前缀描述**【data:image/jpeg;base64,】** |
| type | 是 | 2 | 图像类型，详见参数规定 |

**请求参数示例**

> img\_url=%2FUpLoad%2FTemp%2F597e64e68d264273a4e23e477d472c5b.jpg&type=2

**响应结果**

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| errorcode | 是 | 状态码 ，详见参数规定 |
| msg | 否 | 返回信息 |
| data | 否 | 响应数据 |

以下字段在code为SUCCESS的时候在data参数中返回

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| user\_id | 是 | 用户Id |
| real\_name | 是 | 昵称 |
| head\_img | 否 | 头像图片地址 |
| token | 是 | Token令牌 |

**响应结果示例**

```js
{
    "errorcode": "0",
    "data": "/UpLoad/Temp/597e64e68d264273a4e23e477d472c5b.jpg"
}
```



