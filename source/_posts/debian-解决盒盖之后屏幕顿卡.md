---
title: debian 解决盒盖之后屏幕顿卡
date: 2022-05-12 09:47:05
tags: 
    - linux
---

1. 安装nvidia-driver `sudo apt install nvidia-driver`
2. 在`/etc/environment`下添加 `LIBGL_DRI3_DISABLE=true`
3. 重启
