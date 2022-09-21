## iptables 指令映射

[iptables 指令将容器内部端口映射到外部宿主机端口指南](https://kubesphereio.com/post/the-iptables-directive-is-a-guide-to-mapping-ports-inside-containers-to-ports-on-external-hosts/)

需要执行三条指令，其中就修改两个参数 :

CONTAINERIP=172.18.0.10
INPORT=30090
iptables -t nat -A DOCKER -p tcp --dport ${INPORT} -j DNAT --to-destination ${CONTAINERIP}:${INPORT}
iptables -t nat -A POSTROUTING -j MASQUERADE -p tcp --source ${CONTAINERIP} --destination ${CONTAINERIP} --dport ${INPORT}
iptables -A DOCKER -j ACCEPT -p tcp --destination ${CONTAINERIP} --dport ${INPORT}

${CONTAINERIP} 就是对应容器的 ip 地址，比如我的容器 ip 地址是 172.18.0.2 
容器的 IP 可以通过如下方式查看：
a. 在容器中：ip addr
b. 在宿主机中 : docker inspect 容器名 |grep IPAddress 所以我就把上述的参数换成我的 IP 地址。
${INPORT} 就是要映射出来的端口，我配置的是一个 console 平台，其端口是 30880

## 持续化规则

iptables-persistent

安装 iptables-persistent

$ sudo apt-get install iptables-persistent
持久化规则

$ sudo netfilter-persistent save
$ sudo netfilter-persistent reload

完成上述操作就可以永久打开我们需要的端口了
