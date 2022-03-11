---
title: debian testing xvnc 配置
date: 2022-03-11 15:56:26
tags:
    - Linux
---


记录一下成功配置xrdp + xvnc 下的步骤：

1. `sudo ap install xrdp tigervnc-standalone-server dbus-x11`

2. 改端口号： `sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini`    

3. 改bpp： `sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g'`

4. KDE-plasma的配置
```
# ~/.xsession

unset DBUS_SESSION_BUS_ADDRESS
unset XDG_RUNTIME_DIR
startplasma-x11
export XDG_SESSION_DESKTOP=KDE
export XDG_DATA_DIRS=/usr/share/plasma:/usr/local/share:/usr/share:/var/lib/snapd/desktop
export XDG_CONFIG_DIRS=/etc/xdg/xdg-plasma:/etc/xdg:/usr/share/kubuntu-default-settings/kf5-settings

# ~/.vnc/startup

#!/bin/sh

unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

/usr/bin/startplasma-x11 &
```


