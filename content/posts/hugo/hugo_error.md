---
title: "hugo 遇到的问题"
description: "Welcome to XdpCs’s blog!"
date: "2022-11-29"
tags: ["hugo"]
showComments: true
---

## 问题1

```shell
found no layout file for "HTML" for kind "page": You should create a template file which matches hugo Layouts Lookup Rules for this combination.
```

### 解决方法

```shell
hugo mod clean
hugo server
```