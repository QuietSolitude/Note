# Go的基本知识

第一个程序Hello.go     
-----------------------
go的程序需要放在go文件夹里的src文件夹里。所以我们需要去创建这些文件夹。    
然后在创建文件夹hello里面新建个hello的go文件    

新建一个go文件    
`vim hello.go`    
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello! World")
}
```
可以使用`go run hello.go`, 但是不会生成可执行文件。    
使用`go intall` 包名，在使用`go intall`前，需要在src文件使用`go mod init 根目录(src)`, 这个命令会在src文件夹里创建一个mod.go文件，    
然后会在go文件夹里创建pkg文件夹。    
然后运行`go intall 存放文件的文件名也就是包`，如果在源文件的包里，那么直接运行`go install`   
这个命令会在go文件夹里创建一个bin并将编译好的hello可执行文件放在里面。    

`package main`关键字package是声明一个包的名字，通常同一个包文件下的属于同一个工程文件，同一个包里所有的源文件package的名字都必须一样的，    
最好是包名和该源文件目录名字一样。但是如果使用到main函数那么包的名字就要是main。    

`import "fmt"`关键字import是导入一个包，fmt是实现格式化输入输出的一个包。    
  .操作是让你调用包函数的的时候不用在写前缀。 但是不推荐这么多，因为代码量多了。就不知道调用那个包的函数。        
  `import { . "fmt"}`    
  别名操作是可以使用自定义的名称来代指包名来调用函数。     
  `import { R "fmt"}` ` R.Println()`    


`fmt.Println("Hello! World")`是指调用Println函数打印字符串并换行。如果不换行可以调用Print()函数。    

go语言的占位符    
---------------------------------------------------
%v 只输出所有的值    
`fmt.Printf("%v", a)`    
也可以指定宽度。例如指定填充4个字符宽度%4v    

Printf函数        
-------------------------------------
如果用户指定了格式化变量或多个格式化变量，那么printf函数将顺序把它们替换成响应的值。    
`fmt.Printf("%-15v $%4v\n", "SpaceX", 94)`    
