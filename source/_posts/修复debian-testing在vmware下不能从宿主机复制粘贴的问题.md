---
title: 修复debian testing在vmware下不能从宿主机复制粘贴的问题
date: 2021-08-11 15:13:27
tags:
    - Linux
    - Vmawre
categories:
    - Linux
---

在新版的debian testing（debian 11）中，安装vmware tools的步骤不再需要使用vmware 自带的iso进行安装，直接采用如下步骤即可完整使用复制粘贴

```
sudo apt install open-vm-tools open-vm-tools-desktop
```