---
title: debian NUC 修复没有声音 (Only dummy output)
date: 2022-03-22 09:40:57
tags:
    - linux
---

搞了好久，记录一下过程；系统是INTEL NUC9，声卡是intel自带的

```shell
# 看下具体报错的原因，报错当中就会显示应该去哪个git repo修复
1. sudo dmesg 

2. 按照https://github.com/thesofproject/sof-bin 上面的来安装

3. sudo reboot

```