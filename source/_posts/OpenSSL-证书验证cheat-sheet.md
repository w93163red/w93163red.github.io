---
title: OpenSSL 证书验证cheat sheet
date: 2021-08-08 11:56:53
tags: 
    - OpenSSL
categories:
    - OpenSSL
---

记录一下自己日常开发时候用到的关于OpenSSL 常用的一些命令:

1. 查看证书的相关信息
``` 
openssl x509 -in ca.pem -text -noout
```

2. 查看证书链的所有证书，并全部打印
``` 
openssl crl2pkcs7 -nocrl -certfile bundle.0.pem | openssl pkcs7 -print_certs -text -noout
```

3. 命令行来验证证书链的合法性（可用于self signed certificate)
```
openssl verify -verbose -CAfile <(cat Intermediate.pem RootCert.pem) UserCert.pem
```