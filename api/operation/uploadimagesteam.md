# UpLoadImageSteam - 进件图片上传

**应用场景**

该接口提供进件图片上传，并返回图片临时目录。

**校验签名**

> 否

**接口链接**

> [http://{BaseURL}/Mch/UpLoadImageSteam](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| PaymentChannelId | 否 | SPDB | 进件通道，详见参数规定 |
| picType | 是 | 1 | 进件图片类型，详见参数规定 |
| content | 是 | /9j/4AAQSkZJRgA | jpg格式图片，进行base64编码，去掉前缀描述**【data:image/jpeg;base64,】**；请对图片进行压缩，上传大小限制在1MB以下 |

**请求参数示例**

> content=/9j/4AAQSkZJRgA&picType=1

**响应结果**

| 字段名 | 必填 | 说明 |
| :--- | :--- | :--- |
| errorcode | 是 | 状态码 ，详见参数规定 |
| msg | 否 | 返回信息 |
| data | 否 | 响应数据，临时图片名称 |

**响应结果示例**

```js
{
    "errorcode": "0",
    "data": "e4afb9e8-7db9-4ddb-954c-9b7c28961953.jpg"
}
```



