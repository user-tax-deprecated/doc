[contabo.com](https://contabo.com)

选择欧元支付，价格更便宜

购买的时候写 prefer AMD cpu ，据说性能更好

`cat /proc/cpuinfo`

我一开始是 `Intel(R) Xeon(R) CPU E5-2620` ，然后邮件联系，换成了 `AMD EPYC 7282 16-Core Processor`

用找回密码来登录购买时候填写的邮箱

用 mosh 登录，更快

## vps 测试脚本

简单测试 `curl -so- 86.re/bench.sh | bash`

unixbench 跑分
```
wget --no-check-certificate https://github.com/teddysun/across/raw/master/unixbench.sh
chmod +x unixbench.sh
./unixbench.sh
```

## 初始化

`bash <(curl -s https://cdn.jsdelivr.net/gh/user-tax-dev/docker_dev_build/ubuntu/boot.sh)`

## 配置 ipv6

编辑 `/etc/netplan/01-netcfg.yaml` 把所有的注释的去掉

然后 

`netplan apply`

如果添加了错误的 ipv6 地址，可以用这个命令删除

`/sbin/ip -6 addr del 2001:0db8:0:f101::1/64 dev eth0`

## 查看时间同步的状态

`timedatectl timesync-status`

`journalctl --unit=systemd-timesyncd.service`

## 自动初始化

[什么是 Cloud-Init，为什么这么酷？](https://contabo.com/blog/what-is-cloud-init/)
