# UpLoadImageSteam - 图片上传

**应用场景**

该接口提供图片上传，并返回图片临时目录。

**校验签名**

> 否

**接口链接**

> [http://{BaseURL}/Utility/UpLoadImageSteam](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| content | 是 | /9j/4AAQSkZJRgA | jpg格式图片，进行base64编码，去掉前缀描述**【data:image/jpeg;base64,】** |

**请求参数示例**

> content=/9j/4AAQSkZJRgA

**响应结果**

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| errorcode | 是 | 状态码 ，详见参数规定 |
| msg | 否 | 返回信息 |
| data | 否 | 响应数据 |

**响应结果示例**

```js
{
    "errorcode": "0",
    "data": "597e64e68d264273a4e23e477d472c5b.jpg"
}
```



