---
layout: post
title:  "Golang安装"
date:   2015-05-08 15:40:00
categories: [golang]
excerpt: go golang go入门 go安装 windows
---

* content
{:toc}

#下载
golang官方二进制分发包包括FreeBSD, Linux, Mac OS X (Snow Leopard/Lion),Windows等平台，包括32位、64位等版本。

golang支持交叉编译，也就是说你在32位平台的机器上开发，可以编译生成64位平台上的可执行程序。

`下载地址:` [http://code.google.com/p/go/downloads/list](http://code.google.com/p/go/downloads/list)

#环境变量说明
-	`$GOROOT`:  指向golang安装之后的根目录，windows平台下默认为c:/go，会在安装过程中由安装程序自动写入系统环境变量。
-	`$GOPATH`: 项目所在文件夹。源码放在$GOPATH/src下，go在build（执行`go build xxx.go`）时会扫描$GOPATH/src和$GOROOT/src
-	`$GOARCH`:目标平台（编译后的目标平台）的处理器架构（386、amd64、arm）
-	`$GOOS`:目标平台（编译后的目标平台）的操作系统（darwin、freebsd、linux、windows）
-	`$GOBIN`:指向安装之后根目录下的bin目录，即$GOROOT/bin，windows平台下默认为c:/go/bin，会在安装过程中由安装程序自动添加到PATH变量中

#测试安装结果
创建hello.go文件：

	package main
	
	import "fmt"
	
	func main() {
		fmt.Println("Hello World!")
	}

执行D:\workspace_go\src>go run test.go

运行结果： Hello World!

#其他
-	官网：[http://golang.org/ ](http://golang.org/ )
-	IDE：[GolangIDE](http://code.google.com/p/golangide/)