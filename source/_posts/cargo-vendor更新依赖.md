---
title: cargo vendor更新依赖
date: 2021-10-11 15:51:46
tags: 
    - rust
Categories:
    - rust
---

假设是一个git 依赖，私有源需`CARGO_NET_GIT_FETCH_WITH_CLI=true`:
1. cargo update -p [package] --precise [commit-id]
2. cargo vendor

非git依赖:
1. cargo update -p [package]
2. cargo vendor

