# 官网 CDN 方案设计

## 文件拆分

## user.tax / usr.tax 泛域名跳转

泛域名解析到阿里云 cdn ，可以绑定一个空的 oss 桶

配置 cloudflare 的 15 年证书

然后配置 edge script 如下

```
rewrite('https://user.tax', 'redirect', 301)
```

### user.tax

主站只放 public/ 下的内容以及 index.html & s.js 

上传到阿里云 oss，用阿里云 cdn edge script 做任意路径重写到 /

![](https://raw.githubusercontent.com/gcxfd/img/gh-pages/276bDA.png)

![](https://raw.githubusercontent.com/gcxfd/img/gh-pages/Ru9LWN.png)

[正则语法 PCRE 可以在这里测试](https://regex101.com)

```
if eq(substr($uri, -4, -1), '.ico') {
  set_cache_ttl('path', 99999999)
}
if match_re($uri, '^/$') {
  set_cache_ttl('path', 99999999)
}
if match_re($uri, '^/[^.]+$') {
  rewrite('/', 'break')
}
```

## usr.tax

其他静态文件放到 Backblaze ，域名用 usr.tax

然后配置阿里云 cdn

[对象存储搭配 CF 带宽联盟实现流量免费](https://t.cn/A6SJWf5H)

[单网站在国内国外分别使用不同的 CDN](https://t.cn/A6SIAk5d)

国内流量走 [多吉云](https://www.dogecloud.com) (价格最低的 CDN)

国外放到 Backblaze 然后 配置 Cloudflare CDN

Cloudflare 域名的 SSL/TLS 加密模式为 必须改为 完全 (端到端加密，使用服务器上的自签名证书)，否则会无法使用

![](https://raw.githubusercontent.com/gcxfd/img/gh-pages/RHGO6v.png)

[Using Backblaze B2 with the Cloudflare CDN](https://help.backblaze.com/hc/en-us/articles/217666928-Using-Backblaze-B2-with-the-Cloudflare-CDN)

[Cloudflare Saas 接入 CNAME 流程](https://blog.idc.moe/archives/cloud-flare-for-saas-cname.html)

[通过 CloudFlare 转换规则隐藏 Backblaze B2 的 bucket 路径](https://www.xiaoz.me/archives/17544)

规则名称：随便写
字段：选择“主机名”
运算符 : 选择“等于”
值：填写您在 CloudFlare 上对 B2 的加速域名（你自己的域名）

然后路径选择“重写到 - 选择 Dynamic”，并填写：

concat("/file/bucket", http.request.uri.path)
其中 bucket 改成你自己的存储桶名称，然后选择部署就行了。

优化后
优化前我们的访问路径为：https://b2.domain.com/file/bucket/xxx.txt

优化后的路径为：https://b2.domain.com/xxx.txt

可以看出去除了 file/bucket/

> Backblaze B2 会在请求的响应头中添加以下几个 header 参数：

* x-bz-content-sha1
* x-bz-file-id
* x-bz-file-name
* x-bz-upload-timestamp

虽然影响不大，但是一看这些参数就知道你用的 B2，并且这些参数头一般拿来也没啥用，我们也可以通过 CloudFlare 的重写规则将其去掉。

[将 Backblaze B2 与 Cloudflare CDN 结合使用 – Backblaze 帮助](https://t.cn/A6SiAQxU)

[最佳实践：通过 Cloudflare 页面规则使用自定义缓存加速您的网站](https://t.cn/A6Sip8Je)

[利用 cloudflare 的 API 清除缓存](https://t.cn/A6SigQMw)

## API 服务器隐藏

主机隐藏可以用阿里云 api 网关

https://help.aliyun.com/document_detail/154725.html

## 阿里云 edgescript 

### 泛域名重定向

```
rewrite(concat('https://user.tax',$uri), 'redirect')
```
### 主站重写

if ne(match_re($uri,'\.(png|ico|webmanifest|svg|xml|txt|js)$')) {
rewrite('/', 'break')
}

## 阿里云 OSS-CDN 自动刷新

当 CDN 已经配置好，在 OSS 控制台的『传输管理 → 域名管理』界面可以看到已经出现 “自动刷新“ 开源，点开按钮即可开启

## ~/.config/rclone/rclone.conf 配置

```
[b2-bak]
type = b2
account = 
key = 

[ali]
endpoint = oss-cn-zhangjiakou.aliyuncs.com
type = s3
provider = Alibaba
env_auth = false
access_key_id = 
secret_access_key = 
acl = public-read
```
