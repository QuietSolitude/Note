# Gin学习笔记
  Gin是一个易于使用API的web框架。  

Gin的依赖
-------------
 Gin需要使用go语言来做脚本，所以需要安装go的sdk，按[go的SDK安装](../Go/Go_Install.md)    

安装Gin    
-----------------------------
 1. 安装Gin框架    
   `go install github.com/gin-gonic/gin@latest`    
 
 2. 在工程里创建一个go.mod依赖仓库来存放程序依赖的信息,运行下面的命令。    
   `go mod init 项目文件名 //创建一个go.mod的依赖库，项目会多了一个go.mod文件，存放着项目需要依赖的信息。`     
 3. 在工程中导入Gin的包才可以使用Gin框架功能    
   `import("github.com/gin-gonic/gin")`   
 4. 当导入Gin的包后，我们需要将这个包的依赖添加到go.mod文件里     
    运行`go mod tidy`引用项目需要的依赖增加到go.mod文件里，并清除go.mod文件里项目不需要的依赖。    

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