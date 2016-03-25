# 阿里云OSS

## DEPRECATED

阿里云官方已打包 [aliyuncs/oss-sdk-php](https://packagist.org/packages/aliyuncs/oss-sdk-php)，此仓库废弃

-----

阿里云OSS官方PHP SDK的Composer封装

* 基于[官方PHP SDK开发包(2014-06-25)](http://docs.aliyun.com/?spm=5176.383663.9.7.WhuzGU#/oss/sdk/sdk-download&php)
* 仅修改了配置文件：注释非必须的常量；常量未定义时才定义，避免重新定义。因此可在其它地方配置OSS
* 未使用命名空间，注意是否与其它类库冲突
* 使用composer自动加载后，暴露的类有OSS_Exception, ALIOSS, 实例化ALIOSS对象时定义类MimeTypes, RequestCore

示例

```PHP
$Oss = new \ALIOSS($access_id, $access_key, $hostname);
```

或

```PHP
define('OSS_ACCESS_ID', 'Your access id');
define('OSS_ACCESS_KEY', 'Your access key');
$Oss = new \ALIOSS(null, null, $hostname);
```

Tips:

* 虽然$hostname有默认值（oss.aliyuncs.com），但强烈建议传递该参数，因为该域名目前默认是杭州节点，未来可能会改变
* 域名和节点是多对一的关系，要操作某bucket，必须传递该bucket所在节点的域名
* 若同时使用阿里云ECS且与OSS在同一节点，请使用内网域名，速度快且流量免费
* [各节点域名](http://docs.aliyun.com/?spm=5176.383663.9.11.Bvtco9#/oss/product-documentation/domain-region)
