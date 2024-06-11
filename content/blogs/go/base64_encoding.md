---
title: "encoding/base64"
description: "Welcome to XdpCs’s blog!"
date: "2024-06-11"
tags: [ "Golang" ]
showComments: true
---

## 简介

* base64是一种用64个字符来表示任意二进制数据的方法

## 用途

* 用于在HTTP协议下传输二进制数据
* 用于在URL中传输参数
* 用于加密
* 用于数据校验，数据压缩，数据编码

## Go

在Go语言中，`encoding/base64`包实现了base64编码和解码

它们分别为`base64.StdEncoding`,`base64.URLEncoding`, `base64.RawStdEncoding`, `base64.RawURLEncoding`

### base64.StdEncoding

* 标准base64编码，使用的字符集为`A-Z`，`a-z`，`0-9`，`+`，`/` 以及填充字符`=`，编码后的字符串长度为4的倍数

在接入[sd3](https://platform.stability.ai/docs/api-reference#tag/Generate/paths/~1v2beta~1stable-image~1generate~1ultra/post)
，返回接口的格式为base64.StdEncoding，但是错误的使用了`base64.RawStdEncoding`
，导致解码失败，但是出来的图片经过上传，能在浏览器中显示，但是在代码中一直抛出`error`

### base64.URLEncoding

* URL兼容的base64编码，使用的字符集为`A-Z`，`a-z`，`0-9`，`-`，`_` 以及填充字符`=`，编码后的字符串长度为4的倍数

### base64.RawStdEncoding

* 标准base64编码，使用的字符集为`A-Z`，`a-z`，`0-9`，`+`，`/`，不需要填充字符`=`，编码后的字符串不会做任何填充

### base64.RawURLEncoding

* URL兼容的base64编码，使用的字符集为`A-Z`，`a-z`，`0-9`，`-`，`_`，不需要填充字符`=`，编码后的字符串不会做任何填充

## 例子

```go
package main

import (
	"encoding/base64"
	"fmt"
)

// @Title        main.go
// @Description
// @Create       XdpCs 2024-06-11 10:15
// @Update       XdpCs 2024-06-11 10:15

func main() {
	data := []byte("Hello//")
	// base64.StdEncoding
	dst := make([]byte, base64.StdEncoding.EncodedLen(len(data)))
	base64.StdEncoding.Encode(dst, data)
	fmt.Println("base64.StdEncoding: ", string(dst))
	fmt.Println("base64.StdEncoding len: ", len(dst))

	// base64.RawStdEncoding
	dst = make([]byte, base64.RawStdEncoding.EncodedLen(len(data)))
	base64.RawStdEncoding.Encode(dst, data)
	fmt.Println("base64.RawStdEncoding: ", string(dst))
	fmt.Println("base64.RawStdEncoding len: ", len(dst))

	// base64.URLEncoding
	dst = make([]byte, base64.URLEncoding.EncodedLen(len(data)))
	base64.URLEncoding.Encode(dst, data)
	fmt.Println("base64.URLEncoding: ", string(dst))
	fmt.Println("base64.URLEncoding len: ", len(dst))

	// base64.RawURLEncoding
	dst = make([]byte, base64.RawURLEncoding.EncodedLen(len(data)))
	base64.RawURLEncoding.Encode(dst, data)
	fmt.Println("base64.RawURLEncoding: ", string(dst))
	fmt.Println("base64.RawURLEncoding len: ", len(dst))
}
```