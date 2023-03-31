---
title: "Go Module"
description: "Welcome to XdpCs’s blog!"
date: "2023-01-21"
tags: ["golang"]
showComments: true
---

* 公共模块代理:

```shell
export GOPROXY=https://goproxy.io  
```

同样可以设置为 https://goproxy.cn

* 私有模块代理：

```shell
export GOPRIVATE=git.xxx.com
```

* 初始化：

```shell
go mod init [module 名称]
```

* 检测和清理依赖：

```shell
go mod tidy
```

* 安装指定包：

```shell
go get -v github.com/go-ego/gse@v0.60.0-rc4.2
```

`go mod`下，`go get github.com/go-ego/gse@v0.60.0`
可以跟语义化版本号，也可以跟git的分支`go get github.com/go-ego/gse@master`
,也可以跟git的提交哈希`go get github.com/go-ego/gse@e3702bed2`
`go get`遵循最小版本选择原则，只会下载不超过这个最大版本号，如果使用`go get github.com/go-ego/gse@master`
，下次在下载只会和第一次的一样，无论 master 分支是否更新了代码

* 查看所有可以升级依赖版本：

```shell
go list -u -m all
```

* 更新依赖：

```shell
go get -u
```

* 更新指定包依赖：

```shell
go get -u github.com/go-ego/gse
```

* 更新补丁版本号

```shell
go get -u=patch github.com/go-ego/gse
```

* 指定版本：

```shell
go get -u github/com/go-ego/gse@v0.60.0-rc4.2
```

* 升降级版本号，使用比较运算符控制

```shell
go get github/com/go-ego/gse@`<v0.60.0`
```

**Replace:**

* 使用命令行：

```shell
go mod edit -replace github.com/go-ego/gse = /path/to/local/gse
go mod edit -replace github.com/go-ego/gse = github.com/vcaesar/gse
```

* 直接修改模块文件：

```shell
replace github.com/go-ego/gse => github.com/vcaesar/gse
```

* 移除依赖：

```shell
go mod tidy
```

`go mod edit --droprequire=golang.org/x/crypto`,仅仅修改`go.mod`配置文件的内容

* 查看依赖包：

```shell
go list -m all
go list -m -json all # json 格式输出
```

* 模块配置格式化

```shell
go mod edit -fmt
```

* 常用命令：

```shell
go mod init # 初始化
go mod tidy # 更新依赖文件,移除不需要的包
go mod download # 下载依赖文件
go mod vendor # 将依赖转移至本地的 vendor文件
go mod edit # 手动修改依赖文件
go mod graph # 打印依赖图
go mod verify # 校验依赖
```

在`go mod`模式，如果没有此依赖，在运行`go run main.go`会先去下载此依赖，当然不只是`go run`,`go build`、`go test`
命令也能自动下载相关依赖包

`go mod`不会在`$GOPATH/src`目录下保存相关引用包的源码，而包源码和链接库保存在`$GOPATH/pkg/mod`目录下