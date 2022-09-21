[mosh 安装学习——一个基于 UDP 的 ssh 服务](https://cloud.tencent.com/developer/article/1622455)

`localedef -v -c -i zh_CN -f UTF-8 zh_CN.UTF-8`

https://github.com/mobile-shell/mosh

可以创建 `vps` 的 mosh 脚本如下，放到 `~/.bin/vps` ，并把 `~/.bin` 添加到 PATH

```
#!/usr/bin/env bash

if [ -z "$1" ]; then
arg=/root/.tmux_default
else
arg=${@:1:$#}
fi

vps=$(basename $0)
set -ex
mosh $vps -p 60000:60009 $arg
```
