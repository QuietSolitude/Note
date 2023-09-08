# 列表
什么是列表     
-------------------------
 是指由一系列特定顺序排列的元素组成。这个列表是动态的。      
 当索引是-1时候，就是改列表的最后一个值，这个可以在不知道列表有多长的情况下获取最后一个元素内容。以此类推，-2则是最后第二个元素。      


列表相关的函数     
-------------------------
- **append(元素)**函数是将元素添加在列表末尾。    
```python
motorcycles = ['honda', 'yamaha', 'suzuki']

motorcycles.append('ducati')
print(motorcycles)
```  

- **insert(index，元素)**函数是将元素插入在列表中。
```python
motorcycles = ['honda', 'yamada', 'suzuki']

motorcycles.insert(0, 'Ruro')
print(motorcycles)
```

- **pop()**函数是删除列表末尾中的元素，并返回该元素。    
```python
motorcycles = ['honda', 'yamaha', 'suzuki']

popped_motorcycles = motorcycles.pop()
print(motorcycles)
print(popped_motorcycles)
```
- **pop(index)**函数是根据index来删除列表中的元素，并返回该元素。   
```python
motorcycles = ['honda', 'yamaha', 'suzuki']
first_owned = motorcycles.pop(1)
print(f"The first motorcycles I owned was a {first_owned.title()}.")
```

- **remove(元素)**函数是在不知道元素索引的情况下，根据元素的值来删除元素，不返回元素,如果有多个相同元素，只会删除索引靠前的ige。    
```python
motorcycles = ['honda', 'yamaha', 'suzuki', 'ducati']
print(motorcycles)

motorcycles_value = motorcycles.remove('ducati')
print(motorcycles)
```

del语句        
------------------------
del语句可以删除指定索引的元素,但不返回这个元素（如果只是单单删除元素，考虑使用del语句而不是pop函数）。      
```python
motorcycles = ['honda', 'yamaha', 'suzuki']

del motorcycles[0]
print(motorcycles)
```

[返回Python笔记](README.md) --- [放回后端笔记](../README.md) --- [返回笔记主页](../../../README.md) --- [返回Web笔记](../../README.md)