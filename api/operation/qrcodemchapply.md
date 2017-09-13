# QrCodeMchApply - 商户进件

**应用场景**

该接口提供商户进件资料提交功能。

**校验签名**

> 否

**接口链接**

> [http://{BaseURL}/Mch/QrCodeApply](http://{BaseURL}/OpenPlatform/Login)

**提交方式**

> POST

**请求参数**

| 参数 | 必填 | 示例值 | 说明 |
| :--- | :--- | :--- | :--- |
| PaymentChannelId | 否 | SPDB | 进件通道，详见参数规定 |
| MchId | 是 | 3337512986861568 | 超赢商户号 |
| FullName | 是 | 广州超赢测试33375 | 商户全称 |
| ShortName | 是 | 超赢测试33375 | 商户简称 |
| DealType | 是 | 0 | 经营类型，详见参数规定 |
| Linkman | 否 | 张三 | 联系人 |
| Mobile | 是 | 13800000000 | 联系人手机 |
| Telephone | 否 | 02061016066 | 联系人电话 |
| Email | 是 | yinziqiang@chaoying.com.cn | 联系人邮箱 |
| Licence | 是 | e7e8ae40-450b-4e79-a5f0-c757c38b37dc.jpg | 营业执照临时文件名称，通过进件图片上传获得 |
| LicenceName | 否 | 广州超赢 | 营业执照名称 |
| LicenceCode | 是 | 92520628MA6DQJ8E98 | 营业执照统一社会信用代码 |
| LicenceRegisterCode | 否 | 440122600111698 | 营业执照注册号 |
| LicenceAddress | 否 | 广州市天河区五山路金山大厦南塔303室 | 营业执照经营场所 |
| LicenceBegin | 否 | 2017-01-01 | 营业执照开始时间 |
| LicenceExpires | 否 | 长期 | 营业执照过期时间 |
| LegalPerson | 是 | 张三 | 营业执照法定代表人名称 |
| LegalPersonType | 是 | 0 | 营业执照持有人类型，详见参数规定 |
| LegalPersonCertType | 是 | 0 | 法人证件类型，详见参数规定 |
| LegalPersonImg1 | 是 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 法人身份证正面照临时文件名称，通过进件图片上传获得 |
| LegalPersonImg2 | 是 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 法人身份证背面照临时文件名称，通过进件图片上传获得 |
| LegalPersonImg3 | 否 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 法人手持身份证照临时文件名称，通过进件图片上传获得 |
| LegalPersonCertCode | 是 | 440102201701010000 | 法人证件号码 |
| LegalPersonCertExpires | 否 | 长期 | 法人证件有效期 |
| jyfw | 否 | 零售行业 | 经营范围 |
| zzjgdmzId | 否 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 组织机构代码证照临时文件名称，通过进件图片上传获得 |
| txzzId | 否 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 特殊资质照临时文件名称，通过进件图片上传获得 |
| ProtocolId | 否 | 95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg | 商户协议照临时文件名称，通过进件图片上传获得 |
| AgentId | 否 | 100 | 代理商编号 |
| DealerSN | 否 | 100 | 经销商编号 |
| SalesSN | 否 | 99 | 推广员编号 |
| IndustryId | 是 | 487 | 行业类别编号 |
| ProvinceId | 是 | 190000 | 商铺所在省编号 |
| CityId | 是 | 190100 | 商铺所在市编号 |
| CountyId | 是 | 190104 | 商铺所在区编号 |
| Address | 是 | 五山路金山大厦南塔303室 | 商铺详细地址，不含省市区 |
| flag\_type | 是 | 0 | 商户类型，详见参数规定；0：个体户，1：企业，2：政府及事业单位 |
| BankAccount | 是 | 6200000000000000000 | 结算账户银行卡号 |
| BankId | 是 | 1 | 结算账户银行编号 |
| AccountName | 是 | 张三 | 结算账户开户人名称 |
| AccountType | 是 | 1 | 结算账户类型，详见参数规定；1：企业，2：个人 |
| ContactLine | 是 | 102581000013 | 结算账户银行联行号 |
| BankFullName | 否 | 中国工商银行 | 开户银行名称 |
| BankName | 是 | 中国工商银行股份有限公司广州第一支行 | 开户银行支行名称 |
| BankProvinceId | 是 | BankProvinceId | 结算账户银行所在省 |
| BankCityId | 是 | 190100 | 结算账户银行所在市 |
| IdCardType | 否 | 1 | 结算账户银行卡持卡人证件类型；1：身份证，2：护照（账户类型为企业时AccountType=1，非必填） |
| IdCard | 否 | 440102201701010000 | 结算账户银行卡持卡人证件号码（账户类型为企业时AccountType=1，非必填） |
| BankImgId | 是 | 95b67a47-81e1-4b24-a1dc-07630eebbb41.jpg | 结算账户银行卡照临时文件名称，通过进件图片上传获得 |
| BankMobile | 是 | 13800000000 | 结算账户银行预留手机号 |

**请求参数示例**

> LicenceName=营业执照商户名称&Mobile=15920000000&LicenceBegin=&Licence=e7e8ae40-450b-4e79-a5f0-c757c38b37dc.jpg&BankName=中国工商银行股份有限公司广州第一支行&BankCityId=190100&CountyId=190104&ShortName=超赢测试3337512986861568&flag\_type=0&ProvinceId=190000&LegalPerson=yzq&MchId=3337512986861568&IdCard=440102201701010000&BankProvinceId=190000&BankAccount=6200000000000000000&BankImgId=bank.jpg&BankMobile=15920000000&CityId=190100&FullName=广州超赢测试3337512986861568&LegalPersonCertCode=440102201701010000&SalesSN=99&Linkman=&LicenceCode=92520628MA6DQJ8E99&LicenceRegisterCode=&ContactLine=102581000013&LicenceAddress=&Email=yinziqiang@chaoying.com.cn&AccountName=张三&BankId=1&Telephone=15920000000&Address=五山路金山大厦南塔303室&IndustryId=487&LegalPersonCertExpires=长期&LegalPersonType=0&DealType=0&LicenceExpires=&LegalPersonImg1=95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg&LegalPersonImg2=95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg&LegalPersonImg3=95b67a47-81e1-4b24-a1dc-07630eebbb40.jpg&IdCardType=1&LegalPersonCertType=0&AccountType=2

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
    "data": "199560183554"
}
```



