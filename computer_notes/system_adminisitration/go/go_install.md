# 什么是Go
  Go是一门简单，可靠且高效的静态语言。

# Go的安装

```  
sudo add-apt-repository ppa:longsleep/golang-backports 查看go的版本库
sudo apt update
sudo apt install golang-go

```
安装好了之后输入 go version命令看是否安装成功。    

打开 go modules功能，命令行输入    
` go env -w GO111MODULE=on`    

modules是管理库的依赖。

[System Adminisitration](../system_adminisitration.md) -- [go](go.md)
