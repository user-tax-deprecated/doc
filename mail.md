## 转发收件

[免费的邮件转发](https://forwardemail.net/zh/pricing) ，支持 catch all

## SMTP 发件

DNS 配置如下

```
❯ nslookup -type=txt  _spf.user.tax
_spf.user.tax   text = "v=spf1 ip4:62.171.170.189 ip6:2a02:c207:2098:9386::1 ~all"

❯ nslookup -type=txt  user.tax
user.tax        text = "forward-email=i.user.tax@gmail.com"
user.tax        text = "v=spf1 a mx include:_spf.user.tax include:_spf.google.com include:spf.forwardemail.net ~all"
```
