---
title: rsync 加速迁移home目录
date: 2021-08-05 13:55:16
tags: 
    - Linux
categories:
    - Linux 
---

最近经常需要去迁移home目录，所以记录一下快速迁移home路径使用的命令：
``` 
rsync -e "ssh -p port" -avAXEWSlHh --exclude=dir1 /source /destination --no-compress --info=progress2 --dry-run
```
