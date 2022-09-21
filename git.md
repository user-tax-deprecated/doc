[GPG 安装与使用](https://imtianx.cn/2019/05/29/gpg_an_zhuang_yu_shi_yong)

可以使用下面方式彻底解决，会弹出输入密码弹框

```
brew install pinentry-mac
echo "pinentry-program /usr/local/bin/pinentry-mac" >> ~/.gnupg/gpg-agent.conf
```
