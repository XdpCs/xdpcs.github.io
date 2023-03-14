---
title: "Go-Code-Comment-Standard"
description: "Welcome to XdpCs’s blog!"
date: "2023-03-13"
tags: ["golang"]
showComments: true
---

## 背景

* 当新接手他人的项目，我们很容易不知所措，不知道这个函数的作用是什么，即使有很好的命名规范，这种事情也会时常发生，甚至有时候几个月不碰这个项目，自己再看这个函数，也会有一种云里雾里的感觉
* 如果拥有好的注释，方便我们自己以后维护，也方便后来的同事接手你的项目，不至于对你的代码说这写的是啥，像一坨💩
* 注释看团队，我们团队习惯使用英文，所以都使用英文，只要整个团队统一一个注释语言即可

## 包注释

* 每个包都应有至少一个包注释
* 放置在package之前，来简短描述这个包的功能

```go
// 包的功能介绍

package 包名称
```

## 文件注释

* 每个文件都应有一个文件注释
* 放置在packag之后，需要包含文件名称，文件描述，文件作者及其时间，更新作者及其时间
* 因为在公司正常开发流程中，可能合并分支的时候，只有自己部门的业务主管，有这个权限进行合并代码，如果去看git的日志，如果只看主分支，只会显示主管的id，很难很快落实到每个人上

```go
package 包名称

// @Title        文件名称
// @Description  文件描述
// @Author       作者 日期 时间
// @Update       更新作者 日期 时间
```

## 结构体注释和接口注释

* 每个结构体或接口都应有注释
* 在结构体定义上面，需要有一个对整个结构体的简要介绍
* 结构体内的每个成员变量也需要有注释

```go
// User defines user login info
type User struct {
    UserName string // user's name
    Password string // user's password
}

// IUser defines user function
type IUser interface {
    Login()  // user login into the system
    Logout() // user logout the system
}
```

## 函数和方法的注释

* 每个函数或方法都应有注释
* 需要包含函数或方法名称、函数或方法描述、函数或方法作者及其时间、输入参数及其参数类型和解释、返回参数及其参数类型和解释
* 在函数或方法定义上面，书写下面的注释

```go
// 函数或方法名称
// @Title         函数或方法名称
// @Description   函数或方法描述
// @Author        作者 日期 时间
// @Param         输入参数名 参数类型  "说明"
// @Return        返回参数名 参数类型  "说明"
```

## 代码逻辑注释

* 每个代码块都需要添加注释

```go
// This is my wife's birthday
if birthday == 1118 {
    ...
}
```

## 示例

[示例](https://github.com/XdpCs/Go-Code-Comment-Standard/blob/master/DEMO/main.go)

