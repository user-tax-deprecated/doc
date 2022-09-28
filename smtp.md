vsmtp 密码验证配置

https://vsmtp.rs/

`apt-get install -y sasl2-bin`

edit /etc/default/saslauthd
```
START=yes

MECHANISM="shadow" 
```

run
```
/lib/systemd/systemd-sysv-install enable saslauthd

systemctl enable saslauthd --now
```
