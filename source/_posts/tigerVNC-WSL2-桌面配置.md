---
title: tigerVNC+WSL2 桌面配置
date: 2025-03-24 14:26:09
tags:
    - Linux
categories:
    - Linux 
---

WSL2 下的tigervnc 配置和正常虚拟机下的略有不同。需要调整一下色深的设定来避免部分Desktop Environment 颜色的问题。

1.  下载最新的tigervnc 版本 （1.5.0 开始支持鼠标前后键的返回和前进）并安装[Release TigerVNC 1.15.0 · TigerVNC/tigervnc](https://github.com/TigerVNC/tigervnc/releases/tag/v1.15.0)
2.  按照ArchWiki的2.1走:For a quick start, see the steps below. Users are encouraged to read [**vncserver(8)**](https://man.archlinux.org/man/vncserver.8) for the complete list of configuration options.
    
    1.  Create a password using `vncpasswd` which will store the hashed password in `$XDG_CONFIG_HOME/tigervnc/passwd`. Ensure the file's permission is set to `0600`. If creating vncserver access for another user, you must be logged in as that user before running vncpasswd.
    2.  Edit `/etc/tigervnc/vncserver.users` to define user mappings. Each user defined in this file will have a corresponding port on which its session will run. The number in the file corresponds to a TCP port. By default, :1 is TCP port 5901 (5900+1). If another parallel server is needed, a second instance can then run on the next highest, free port, i.e 5902 (5900+2).
    3.  Create `$XDG_CONFIG_HOME/tigervnc/config` and at a minimum, define the type of session desired with a line like `session=foo` where foo corresponds to whichever [**desktop environment**](https://wiki.archlinux.org/title/Desktop_environment) is to run. One can see which desktop environments are available on the system by seeing their corresponding _.desktop_ files within `/usr/share/xsessions/`. For example:
    
    ```
    session=lxqt
    geometry=1920x1080
    localhost
    alwaysshared
    ```
    
      
    我自己的配置
    
    ```
    session=gnome
    geometry=1920x1080
    depth=32
    localhost
    alwaysshared
    ```
    
3.  注册systemd服务 `sudo cp /usr/lib/systemd/system/vncserver@.service /etc/systemd/system/vncserver@.service`
4.  配置自动启动`sudo systemctl enable vncserver@:1.service`
5.  验证下vncserver是否正确启动`sudo lsof -i` 。如果没有修改的话，看到590x 即成功。

## Reference

[TigerVNC - ArchWiki](https://wiki.archlinux.org/title/TigerVNC)

[第 13 章 tigervnc | Red Hat Product Documentation](https://docs.redhat.com/zh-cn/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-tigervnc#sec-configuring-vncserver-2users)