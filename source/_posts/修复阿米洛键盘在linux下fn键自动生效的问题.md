---
title: 修复阿米洛键盘在linux下fn键自动生效的问题
date: 2021-08-01 13:33:35
tags: 
    - 配置
    - Linux
categories:
    - Linux 配置
---

换上阿米洛键盘之后，发现在linux下fn 键自动锁定了，导致F1-F12的键都不能用了，很不方便。因为我F12键绑定了yakuake了。然后想用evtest把scan code读出来，然后自己修改（[可以这篇文章](https://www.bilibili.com/read/cv5156572)）。发现第一排键没有scan code……尴尬。。

后来在继续搜索的时候，发现可能被识别成apple 键盘了，导致fn 被锁定。于是直接做如下修改：

临时（重启之后会失效）:

禁用fn （也就是变成fn+f键触发对应的效果）

`echo 0 | sudo tee /sys/module/hid_apple/parameters/fnmode`

启用fn：

`echo 1 | sudo tee /sys/module/hid_apple/parameters/fnmode`


永久：

```
echo options hid_apple fnmode=0 | sudo tee -a /etc/modprobe.d/hid_apple.conf
sudo update-initramfs -u -k all
```