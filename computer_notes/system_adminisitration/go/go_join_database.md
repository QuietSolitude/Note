# 使用go语言连接数据库

使用docker来安装mariadb数据     
----------------------------
- 使用docker安装mariadb
`docker run --name some-mariadb --env MARIADB_ROOT_PASSWORD=密码  mariadb:latest`      
`--env`的功能是设置环境变量，格式是–env 环境变量=值，以上的命令环境变量叫 MARIADB_ROOT_PASSWORD是指mariadb数据库用户root以及它的密码，这是mariadb的镜像规定的变量，mariadb镜像就可以读取这个变量的值来设置root密码。

- 运行容器并映射mariadb数据库的端口，数据库默认的端口是3306    
`docker run  -p 3306:3306  --env MARIADB_ROOT_PASSWORD=密码 mariadb`           

连接数据库        
--------------------------
`mysql -hlocalhost -P3306 -uroot -p密码 --protocol tcp` 连接数据库 这里登录的密码是指mariadb容器的密码一样。    

创建数据库和表    
--------------------------
- 创建数据库    
  `create database 数据库名`    
- 创建表
  `create table 表名`
需要注意的是，在创建表的成员属性的时候，在要指定的属性语句必须在要在指定的属性后面，不然会报错。例如下面指定user_id为主键的例子：        
```go
create table students(
	user_id INT NOT NULL AUTO_INCREMENT,
	PRIMARY KEY (user_id),
	username VARCHAR(100) NOT NULL,
	sex VARCHAR(40) NOT NULL,
	email VARCHAR(100) NOT NULL		
);     创建表时，主键primary key要放在要设定的主键下面。
```
编写GO程序来连接数据库并对数据库进行操作
---------------------------------------------
- 什么是sqlx库和driver库？
  sqlx库是go语言内置的连接数据库的库。   
  driver包定义了应被数据库驱动实现的接口，这些接口会被sqlx包使用。    

- 安装sqlx库和driver库   
  - 安装sqlx库   
    在项目中使用以下go get命令来安装sqlx库      
    `go get github.com/jmoiron/sqlx`
    在代码中import导入sqlx包，才可以使用这个库。    
    `import ("github.com/jmoiron/sqlx") `      

  - 安装driver库    
    `go get -u github.com/go-sql-driver/mysql`   
    以上的命令是安装driver库，也要在代码中import导入driver包，才可以使用这个库。    
    但是要注意的是mysql包比较特殊，指允许调用包里的init函数，其他函数不允许调用。所以要在导入的包名前面加_下划线。     
    `import(_ "github.com/go-sql-driver/mysql")`   

使用go来对数据库增加一个数据。代码如下。    
----------------------------------------
```go
package main

import (
	"fmt"

	_ "github.com/go-sql-driver/mysql"

	"github.com/jmoiron/sqlx"
)
//创建一个结构
type Persion struct {
	UserId   int    `db:"user_id"`
	Username string `db:"username"`
	Sex      string `db:"sex"`
	Email    string `db:"email"`
}

//创建一个全局变量的数据库对象
var Db *sqlx.DB

func init() {
	//Open函数返回值一个返回值是连接好的数据库对象，另一个返回值是连接时出现的错误。如果错误err不为空，否则为空。这是go语言的错误处理机制。
	//连接数据库
	database, err := sqlx.Open("mysql", "root:test@tcp(localhost:3306)/test")
	//nil是go语言里的零值
	if err != nil {
		fmt.Println("打开数据库失败， err: ", err)
		return
	}
  
	//初始化数据库
	Db = database

}

func main() {
	//Exec函数可以执行数据库的insert, update, delete命令。
	//返回的是修改好的集，和是否修改成功。
	r, err := Db.Exec("insert into students (username,sex,email) value(?,?,?)", "stu02", "girl", "stu01@qq2.com")

	if err != nil {
		fmt.Println("修改失败，err:", err)
		return
	}

  //获取插入数据的Id
	id, err := r.LastInsertId()

	if err != nil {
		fmt.Println("修改失败，err:", err)
		return
	}
  
	fmt.Printf("修改成功，修改了第%d个数据", id)
}

```
[System Adminisitration](../system_adminisitration.md) -- [go](go.md)

