https://blitiri.com.ar/p/chasquid/install/

apt-get install -y acl
setfacl -R -m u:chasquid:rX /mnt/www/.acme.sh

chasquid-util user-add i@user.tax

for i in dkimsign dkimverify dkimkeygen; do
  go install github.com/driusan/dkim/cmd/$i@latest
done

配置好证书之后

chown chasquid:chasquid -R /etc/chasquid

systemctl restart chasquid
systemctl enable chasquid --now

---

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
