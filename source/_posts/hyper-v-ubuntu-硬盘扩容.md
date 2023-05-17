---
title: hyper-v ubuntu 硬盘扩容
date: 2023-05-17 17:19:39
tags:
    - linux
    - Hyper-V
---

在hyper-v设置硬盘扩容之后，在Linux下操作：

```shell
sudo apt install cloud-guest-utils
sudo growpart /dev/sda 1
sudo resize2fs /dev/sda1
```