# Log in to Huawei Cloud SWR
使用此GitHub Action登录到华为云容器镜像服务[SWR(SoftWare Repository for Container)](https://support.huaweicloud.com/swr/)。登录完成之后，workflow中其他操作步骤可以执行镜像构建、镜像推送、镜像拉取等操作。


## Action参数  
> 提示：下面参数标注 🔐 的参数属于敏感信息，建议在GitHub项目的setting--Secret--Actions下添加私密参数。

| Name          | Sensitive | Require | Description |
| ------------- | ------- | ------- | ----------- |
| access-key-id    |   🔐    |   true      | 华为云访问密钥ID即AK,可以在[我的凭证](https://support.huaweicloud.com/usermanual-ca/ca_01_0003.html?utm_campaign=ua&utm_content=ca&utm_term=console)获取。|
| access-key-secret    |   🔐    |    true     | 华为云访问密钥即SK,可以在[我的凭证](https://support.huaweicloud.com/usermanual-ca/ca_01_0003.html?utm_campaign=ua&utm_content=ca&utm_term=console)获取。|
| region    |           |     true   | 华为云区域，可以在[我的凭证](https://console.huaweicloud.com/iam/?locale=zh-cn#/mine/apiCredential)获取|

## 参考实例

```yaml
- uses: huaweicloud/swr-login@v2.0.0
  with:
    access-key-id: ${{ secrets.ACCESSKEY }} 
    access-key-secret: ${{ secrets.SECRETACCESSKEY }}
    region: '<region id>'  # example: cn-north-4
```
详情可参考 [swr-login-workflow-samples](https://github.com/huaweicloud/swr-login-workflow-samples)


## Action中使用的公网地址说明
本action是华为云SWR鉴权, 根据用户使用region参数涉及到对应region的华为云iam服务终端节点的公网域名
```
1. 华北-北京一	    https://swr-api.cn-north-1.myhuaweicloud.com	
2. 华北-北京二	    https://swr-api.cn-north-2.myhuaweicloud.com		
3. 华北-北京四	    https://swr-api.cn-north-4.myhuaweicloud.com
4. 华东-上海二	    https://swr-api.cn-east-2.myhuaweicloud.com	
5. 华东-上海一	    https://swr-api.cn-east-3.myhuaweicloud.com
6. 华南-广州	      https://swr-api.cn-south-1.myhuaweicloud.com	
7. 华南-深圳	      https://swr-api.cn-south-2.myhuaweicloud.com	
8. 西南-贵阳一	    https://swr-api.cn-southwest-2.myhuaweicloud.com
```