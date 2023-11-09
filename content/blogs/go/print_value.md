---
title: "Go打印结构体指针中的具体内容，而无需实现String()方法"
description: "Welcome to XdpCs’s blog!"
date: "2023-11-09"
tags: [ "Golang" ]
showComments: true
---

## 痛点

### 例子

```go
package main

import "fmt"

type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
}

func main() {
	t := &TreeNode{
		Val: 1,
		Left: &TreeNode{
			Val: 2,
		},
		Right: &TreeNode{
			Val: 3,
		},
	}
	fmt.Println(t)
}
```

### 输出

```text
&{1 0x14000126018 0x14000126030}
```

我们从上述的例子可以看到，我们无法打印出结构体内部的Left和Right，只能打印出他们的地址

## 解决办法

### 使用程序库

[https://github.com/XdpCs/print-value](https://github.com/XdpCs/print-value)

### 例子

```go
package main

import (
	"fmt"

	print "github.com/XdpCs/print-value"
)

type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
}

func main() {
	t := &TreeNode{
		Val: 1,
		Left: &TreeNode{
			Val: 2,
		},
		Right: &TreeNode{
			Val: 3,
		},
	}
	fmt.Println(print.Print(t))
}
```

### 结果

```text
TreeNode{Val:1,Left:TreeNode{Val:2,Left:nil,Right:nil},Right:TreeNode{Val:3,Left:nil,Right:nil}}
```
