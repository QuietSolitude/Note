# Python里的String的有关方法和操作

f字符串（format）    
--------------------
 是将两个字符串的变量插入的变量中。     
 格式是 变量 = f"{字符串的变量} {字符串的变量}"      
 ```python
first_name = "ada"
last_name = "lovelace"
full_name = f"{first_name} {last_name}"

print(full_name.title())
print(f"Hello! {full_name.title()}!")

message = f"Hello! {full_name.title()}!"
print(message)
 ```

常用的函数     
-------------------------
- title()函数是让每个单词第一个字母变成大写。    
- upper()函数是将所有的字母都变成大写。   
- lower()函数是将所有的字母都变成小写。
- rstrip()函数删除字符出右边的空格，并返回这个字符串。    
- lstrip()函数删除字符串左边的空格，并返回这个字符串。
- strip()函数删除字符串两边的空格，并返回这个字符串。
- removeprefix(要删除的字符串段)函数删除字符串的前缀，并返回这个字符串。
- removesuffix(要删除的字符串段)函数删除字符串的后缀，并返回这个字符串。

[返回Python笔记](README.md) --- [放回后端笔记](../README.md) --- [返回笔记主页](../../../README.md) --- [返回Web笔记](../../README.md)