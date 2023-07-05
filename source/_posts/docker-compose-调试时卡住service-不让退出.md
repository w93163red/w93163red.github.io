---
title: docker compose 调试时卡住service 不让退出
date: 2023-07-04 20:40:15
tags:
    - docker
---

在service的下方加入这两行：
```
    tty: true
    command: tail -F /dev/null
```