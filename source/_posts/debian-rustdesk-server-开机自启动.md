---
title: debian rustdesk-server 开机自启动
date: 2022-05-12 09:59:40
tags:
    - linux
---

1. clone rustdesk-server-demo `https://github.com/rustdesk/rustdesk-server-demo.git`
2. 提前编译好 `cargo build`
3. 写一个脚本 `run_rustserver.sh` ，内容如下：
`IP=192.168.50.77  /home/ling/code/rustdesk-server-demo/target/debug/rustdesk-server`
4. 在`/etc/systemd/system`下，创建一个rustdesk-server.service 文件，内容如下：
```
[Unit]
Description=Rust Server

[Service]
Type=simple
ExecStart=/bin/bash /home/ling/run_rustserver.sh

[Install]
WantedBy=multi-user.target 
```
5. `chmod 0644 rustdesk-server.service`
6. `systemctl enable rustdesk-server.service`