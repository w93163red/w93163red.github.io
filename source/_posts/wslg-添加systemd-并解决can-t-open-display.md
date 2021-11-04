---
title: wslg 添加systemd 并解决can't open display 以及安装microk8s
date: 2021-11-04 11:00:03
tags:
    - wslg
---


1. `git clone https://github.com/DamionGans/ubuntu-wsl2-systemd-script`
2. `bash ubuntu-wsl2-systemd-script.sh`

使用zsh的情况下，需要在zshrc添加`source /usr/sbin/start-systemd-namespace`，使得systemd 自动载入
因为引入systemd之后会把wslg的X11 的东西弄挂，需要重新连一次
```
export DISPLAY=:0
sudo rm -rf /tmp/.X11-unix
ln -s /mnt/wslg/.X11-unix /tmp/.X11-unix
```

之后就可以正常的`sudo snap install microk8s --classic`。

如果安装microk8s安装失败，`sudo apt purge snapd && sudo apt install snapd`