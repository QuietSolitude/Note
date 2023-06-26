# Linux常用的命令

如果需要查询命令的用法可以使用man或者help来查询。    
`man 要查询的命令`    
eg. man date    
![tu](images/man_date.png "man date")    
在图里面的DATE(1)    
数字1是指使用者在shell环境中可以操作的指令或可执行的文件。    
数字5是指配置文件或是某些文件的格式。
系统管理员可用的管理指令。    

ls命令是列出当前文件。    
ls -al 是列出所有的文件详细的权限与属性（包含隐藏文件，.开头的文件就是隐藏文件）。       

查看网络的连接状态可以使用`netstat -a `    

查看后端运行程序可以使用`ps-aux`     

Linux关机：    
- 将数据同步写入硬盘的指令:`sync`    
- 惯用的关机命令：`shutdown`    
  - -r 是将服务器关闭后在重新启动。`shutdown -r 20 二十分钟后关机重启`    
  - h 将系统的服务停掉后立即关机。 `shutdown -h 10 "十分钟后关机"`      
- 重启使用 `reboot` 

cp命令    
-----------------------
  cp命令是将想要的文件或者目录的所有文件拷贝到另一个文件或者目录里。    
  语法：`cp [选项] 源文件或目录 目标文件或者目录` 
  选项的含义：    
   - a 在拷贝目录时使用，保留链接、文件属性，并递归地拷贝目录。    
   - d 拷贝时保留链接。    
   - f 删除已近存在的目标文件而不提示。    
   - i 在覆盖目标文件之前将给出提示，如果确认文件才会被覆盖。    
   - p 复制源文件的内容外，还将把其修改时间和访问权限都复制到新文件中。    
   - r 若给出的源文件是目录文件，就将该目录所有的文件和子目录都复制到另一个目录中。   
   - l 不做拷贝，只是链接文件。  

tar命令
----------------------------
  tar是压缩或者解压文件的命令，tar压缩文件一般都是以tar.gz为结尾。    
  语法：`tar [选项] 压缩名.后缀 文件夹名`
  选项的含义：     
   - c 建立压缩档案    
   - x 解压
   - t 查看内容
   - r 向压缩归档文件末尾追加文件
   - u 更新原压缩包中的文件    
  
  这五个是独立的命令，压缩解压都要用到其中一个，可以和别的命令连用但只能用其中一个。       
  下面的参数是根据需要在压缩或解压档案时可选的。    
   - z 有gzip属性的
   - j 有bz2属性的 
   - Z 有compress属性的 
   - v 显示所有过程    
   - O 将文件解开到标准输出
  
  参数-f是必须的    
   - f 使用档案名字，切记，这个参数是最后一个参数，后面只能接档案名。

  下面的例子参考：    
  `tar -cf all.tar *.jpg //这条命令是将所有.jpg的文件打成一个名为all.tar的包。-c是表示产生新的包，-f指定包的文件名。`    
  `tar -rf all.tar *.gif // 这条命令是将所有.gif的文件增加到all.tar的包里面去。-r是表示增加文件的意思。`     
  `tar -uf all.tar logo.gif //这条命令是更新原来tar包all.tar中logo.gif文件，-u是表示更新文件的意思。`     
  `tar -tf all.tar //这条命令是列出all.tar包中所有文件，-t是列出文件的意思`     
  `tar -xf all.tar // 这条命令是解出all.tar包中所有文件，-x是解开的意思`       
  `tar -tf aaa.tar.gz    //在不解压的情况下查看压缩包的内容`     

  压缩：    
  `tar –cvf jpg.tar *.jpg //将目录里所有jpg文件打包成tar.jpg`     
  `tar –czf jpg.tar.gz *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用gzip压缩，生成一个gzip压缩过的包，命名为jpg.tar.gz`
  `tar –cjf jpg.tar.bz2 *.jpg //将目录里所有jpg文件打包成jpg.tar后，并且将其用bzip2压缩，生成一个bzip2压缩过的包，命名为jpg.tar.bz2`
  `tar –cZf jpg.tar.Z *.jpg   //将目录里所有jpg文件打包成jpg.tar后，并且将其用compress压缩，生成一个umcompress压缩过的包，命名为jpg.tar.Z`

  解压：    
  `tar –xvf file.tar //解压 tar包`
  `tar -xzvf file.tar.gz //解压tar.gz`
  `tar -xjvf file.tar.bz2   //解压 tar.bz2`
  `tar –xZvf file.tar.Z //解压tar.Z`