# 第五讲 : 字典

[TOC]

## 字典类型定义

字典类型定义

1. **字典是键值对的集合**，键值对之间没有顺序且不能重复[字典也是一种集合]

2. 采用大括号{}和dict()创建，建立模式如下：
   {<键1>:<值1>, <键2>:<值2>, … , <键n>:<值n>}，**其中键和值通过冒号连接，不同键值对通过逗号隔开**。

3. 字典是包含0个或多个键值对的集合，**没有长度限制**，可以根据键索引值的内容。

```python
>>> s={"中国":"北京","美国":"华盛顿"}
>>> s["中国"]
'北京'
>>> s["中国"]="北京北京"
>>> print(s)
{'中国': '北京北京', '美国': '华盛顿'}
>>> s
{'中国': '北京北京', '美国': '华盛顿'}
```

### 词典的创建和删除
```
dictionary = {'key1':'value1','key2':'value2',...,}
```
很容易想到字典的关键在于“键-值对”，“键”是索引，“值”即是键索引的内容。
引入**创建字典的函数**：```dictionary = dir(zip(list1,list2))```，list1做键，2做值，如果list1和list2的长度不同，则最后的结果长度与最短的一致，例：
```python
name = ['张三','李四','王五']
age = ['19','20','18']
dictionary = dict(zip(name,age))#转换为字典，如果不用dict转换则其保持不可读的生成器模式
print(dictionary)
```

输出结果：
```
{'张三': '19', '李四': '20', '王五': '18'}
```
也可以通过给定的键值对创建字典
```python
dictionary = dict(key1=value1,key2=value2,...,)
```
还可以使用函数fromkeys()创建只有键的空字典
```python
name = ['张三','李四','王五']
dictionary = dir.fromkeys(name)
print(dictionary)
```
输出：
```
{'张三': None, '李四': None, '王五': None}
```
使用dictionary.clear删除字典元素

### 字典的访问——键值对

判断访问的方法有两种：

* if判断处理

  ```python
  dictionary = {'张三': '19', '李四': '20', '王五': '18'}
  print(dictionary['张三'] if '张三' in dictinoary else '字典无此人')
  ```

* get()指定获取
  
    ```python
    dictionary.get(key,[default])
    ```

### 字典的遍历

Python提供了items()函数用于字典的遍历：
```python
for item in dictionary.items():
	print(item)
```
这样得到的将是一个元组，若想获取各个具体的键和值，可以使用下列代码：
```python
dictionary = {'张三': '19', '李四': '20', '王五': '18'}
for key,value in dictionary.items():
	print(key,"的年龄是",value)
```
执行结果：
```python
张三 的年龄是 19
李四 的年龄是 20
王五 的年龄是 18
```
Python还提供了values()和keys()方法专门获得值和键，用法与上述遍历一致

### 添加、修改和删除字典元素

* 添加元素格式：
    ```python
    dictionary[key] = value #会添加到末尾

* 修改元素：只需给它直接赋新的value，当元素存在时即相当于修改功能

* 删除元素（这里直接介绍开发中最保险的方法——加入条件判断）

  ```python
  dictionary = {'张三': '19', '李四': '20', '王五': '18'}
  if '李四' in dictionary:
  	del dictionary['张三']
  print(dictionary)
  ```

### 字典推导式
推导式我们已经遇到了很多，字典推导式依旧和前面保持一致，直接上代码格式：
```python
import random
randomdict = {i:random.randint(10,100) for i in range(1,5)} #创建字典
print(randomdict)
```

### 字典类型的函数和方法

|函数或方法	|描述|
|:--:|:--:|
|del d[k]	|删除字典d中键k对应的数据值|
|k in d	|判断键k是否在字典d中，如果在返回True，否则False|
|d.keys()|	返回字典d中所有的键信息|
|d.values()|	返回字典d中所有的值信息|
|d.items()	|返回字典d中所有的键值对信息|
|d.get(k,default)|	键k存在，则返回相应值，不在则返回default|
|d.pop(k,default)|	键k存在，则取出相应值，不在则返回default|
|d.popitem()	|随机从字典d中取出一个键值对，以元组形式返回|
|d.clear()	|删除所有的键值对|
|len(d)	|返回字典d中元素的个数|

代码演示：

```python
>>> s={"中国":"北京","美国":"华盛顿","法国":"巴黎"}
>>> del s["美国"]
>>> s
{'法国': '巴黎', '中国': '北京'}
>>> "中国" in s
True
>>> s.keys()
dict_keys(['法国', '中国'])
>>> s.values()
dict_values(['巴黎', '北京'])
>>> s.items()
dict_items([('法国', '巴黎'), ('中国', '北京')])
>>> s.get("中国","无信息")
'北京'
>>> s.get("美国","无信息")
'无信息'
>>> s.pop("法国","无信息") # pop自动出栈
'巴黎'
>>> s
{'中国': '北京'}
>>> len(s)
1
>>> s.clear()
>>> s
{}
>>> len(s)
0
```

