---
title: "Fix Openssl Library Version"
slug: "fix-openssl-library-version"
date: 2023-04-13T11:10:43+08:00
draft: false
tags: []
categories: []
---

# 解决更新 OpenSSL 之后 Library 没有对应加载最新版本的问题

解决方案来自

https://github.com/openssl/openssl/issues/18025

以下为实施成功的方法摘录

Step by step fix for debian related OS based on tmshort answer:

make sure libraries are indeed found in /usr/local/lib64 

```
ls /usr/local/lib64/
# >>  libcrypto.so.3  libssl.a  libssl.so ...
```

make sure the libraries path is missing from cat `/etc/ld.so.conf.d/*` output

configure the new path

```
# add it
sudo echo /usr/local/lib64/ >  /etc/ld.so.conf.d/openssl.conf
# load it
sudo ldconfig
```

you should see `/usr/local/lib64` in the list

```
ldconfig -v |less
```

confirm openssl is working

```
openssl version
#> OpenSSL 3.1.0 14 Mar 2023 (Library: OpenSSL 3.1.0 14 Mar 2023)
```
