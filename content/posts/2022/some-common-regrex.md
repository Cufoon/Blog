---
title: "Some Common Regrex"
slug: "some-common-regrex"
date: 2022-07-15T14:19:15+08:00
draft: false
tags: []
categories: []
math: false
---

# 匹配网址

## 匹配裸网址

如：

- http://xxx.yyy
- http://xxx.yyy/
- https://xxx.xxx.yyy
- https://xxx.xxx.yyy/

```javascript
const re = /^https?:\/\/([A-Za-z0-9-_]+\.)+[A-Za-z0-9]+\/?$/i;
```
 
 
 
## 匹配文件

如：
- http://xxx.yyy/index.html
- https://xxx.yyy/sw.js
- https://xxx.yyy/sw.js?mmm=nnn&ss=b

```javascript
const re =
  /^https?:\/\/([A-Za-z0-9-_]+\.)+[A-Za-z0-9]+\/(sw\.js|index\.html)(\?.*)?$/i;
```
