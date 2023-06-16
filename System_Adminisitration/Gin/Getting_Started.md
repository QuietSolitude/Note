# Gin学习笔记
  Gin是一个易于使用API的web框架。  

Gin的依赖
-------------
 Gin需要使用go语言来做脚本，所以需要安装go的sdk，按[go的SDK安装](../Go/Go_Basic_Knowledge.md)  
 

Gin的基础
------------------

```go
package main

import "github.com/gin-gonic/gin"

func main() {
	engine := gin.Default()

	engine.GET("/hello", func(context *gin.Context) {
		context.JSON(200, gin.H{
			"message": "Hello ares!",
		})
	})

	engine.Run()
}

```

Engine是一个容器对象，是整个框架的基础。    

如何初始化Gin的实例：    
使用gin.Defualt()方法来初始化，Defualt方法会增加使用Logger和Recovery自带中间件的处理。    
  Logger是负责进行打印并输出日志的中间件,方便开发者进行程序调试;     
  Recovery中间件的作如果程序执行过程中遇到panc中断了服务,则Recovery会恢复程序执行,并返回服务器500内误。    
  panc是指宕机。    
Get是HTTP协议中的4个请求方法之一，用来获取资源。    
gin.Context是允许我们在中间件之间，传递变量，管理流程，验证请求的JSON并呈现JSON响应。    