# science-net

science-net: 科学网络！部署需要的资源如下：

购买资源：
    - 域名
    - 云主机

免费资源：
    - 域名证书

# 准备工作

## 云主机

科学网络的核心就是云主机，云主机便宜、高带宽、不限制流量这3个条件根据自身需求进行平衡，针对CPU、内存、磁盘并不是科学上网云主机的核心需要。目前，首推阿里云轻量云服务器、腾讯云轻量云服务器。

## 域名

域名建议在海外GoDaddy、Cloudflare、nameslio等服务商购买，海外服务商不需要实名。

## 域名证书

域名证书建议使用Let's Encrypt，证书有效期90天，推荐使用`acme.sh`工具进行证书颁发，并且配置脚本进行自动续签。

# 使用说明

以上域名、云主机准备完成后，接下来部署科学网络：

## 颁发证书

1. 安装`acme.sh`

```bash
curl https://get.acme.sh | sh -s email=my@example.com
```

2. 使用[DNS API](https://github.com/acmesh-official/acme.sh/wiki/dnsapi)方式颁发证书

**Cloudflare示例：**

获取API Key：

```bash
export CF_Key="763eac4f1bcebd8b5c95e9fc50d010b4"
export CF_Email="alice@example.com"
```

颁发证书
    - 请将`example.com`修改为用户购买的域名
    
```bash
acme.sh --issue --dns dns_cf -d example.com -d '*.example.com' -k 2048
```
