---
title: Oracle JDK 1.8 ubuntu 安装
date: 2021-11-03 20:43:32
tags:
    - Linux
    - Java
categories: 
    - Linux
---

1. `sudo mkdir -p /usr/lib/jvm`
2. `sudo tar zxvf jdk-version-linux-x64.tar.gz -C /usr/lib/jvm`
3. `sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0_version/bin/java" 1`
4. `sudo update-alternatives --set java /usr/lib/jvm/jdk1.8.0_version/bin/java`

