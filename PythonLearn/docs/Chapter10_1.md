# 第十一讲 ：技巧讲解

[TOC]



### 注释
单行注释：以 # 开头，编程规范建议#后面跟一个空格
多行注释：用一对连续的三个引号，单引号或者双引号均可（"""/’’’）

```python
# 单行注释

'''多行注释'''
	或者
"""多行注释"""

```

### 行与缩进
1. python与其他语言明显的区别是没有大括号，而是用缩进表示代码块。
2. 需要注意每行语句不需要以分号结束。（学过c语言的应该注意一下）
2. **对于Python，行尾的冒号和下一行的缩进表示一个代码块的开始，而缩进结束则代表一个代码块的结束。**

### 编码规范

1. 每个import语句只导入一个模块

   ```python
   #推荐写法
   import A
   import B
   ```

2. 行尾不要加分号，Python的语句不需要 ; 结尾

3. 为了提高可读性，通常在顶级定义之间空两行，方法定义空一行，某些功能的位置也可以空一行

4. 命名规范 

   * **模块名称**：小写字母加中部下划线 game_main,game_register
   * **类名**：Pascal命名法，即首字母大写
   * **模块内部的类**："_" + 标识符，如BorrowBook的内部类使用_BorrowBook
   * **常量命名**：全部采用大写字母，可以使用下划线
   * **单下划线开头的模块变量或函数受保护，双下划綫开头的实例变量或方法是类私有的**

### Python中特有的交换两个变量的值的方法
直接将a， b两个变量放到元组中，再通过元组按照index进行赋值的方式进行重新赋值给两个变量。**（不用再用一个中间值进行交换了）**

代码：
```python
a=1
b=2
(a,b)=(b,a)
print(a)
print(b)
```
结果：
```
2
1
```

### 循环的巧应用（列表解析）
当你要建立一个1到10所有数字的平方时：

普通方法：
```python
list=[]
for i in range(1,11):
    list.append(i**2)
print(list)
```
结果：
```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
列表解析：
```python
list=[i**2 for i in range(1,11)]
print(list)
```
结果：
```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
总结：
1. 可以看出，**只需要将普通方法中的append后面括号里加上普通方法中的for i in range(1,11)加到列表里即可**

2. 也就是普通方法经过复制粘贴是可以形成列表解析的，但并不是所有的for循环可以写成列表解析式

### eval（）函数与str（）函数
**eval(<字符串>)的作用是将输入的字符串转变成Python语句。
str() 函数将整形转化为字符串形式.**
注意：
**无论用户在控制台输入什么内容，input()函数都以字符串类型返回结果**

代码展示：
```python
x=eval(input("输入数字"))  
print(x)
print(x*2)
print(type(x)) 
x=str(x)     #此时x转变成了字符串形式
print(type(x))
```
结果：
```
输入数字6
6
12
<class 'int'>
<class 'str'>
```
如果不加eval()函数会出现如下情况：
```python
x=input("输入数字")
print(x)
print(x*2) #会出现字符串“6”+“6”=“66”
print(type(x))
```
结果：
```
输入数字6
6
66
<class 'str'>
```
注意：
1. 使用eval()函数处理字符串需要合理使用，假如你直接输入字符串“Hello”，eval()函数会去掉两个引号，这时候将其解释为一个变量，而之前又没有定义过Hello变量，解释器会报错.

2. 若对“‘Hello"'使用eval()函数，仅仅会去掉外层的双引号，还会留下一对单引号，此时’Hello‘会被解释为字符串。

### 条件表达式的紧凑形式
语法：
```
<表达式1> if <条件> else <表达式2>
条件成立则输出表达式1，不成立则输出表达式2
```
代码：
```python
guess=eval(input())
print("你猜{}了".format("对" if guess==99 else "错"))
```
结果：
```python
99
你猜对了
```

### try-except语句的应用

Python使用try-except语句来实现异常处理，其基本语法格式如下：

```python
try：
     <语句块1>
except <异常类型>:
    <语句块2>
```

代码演示：

```python
try:
    num=eval(input("请输入一个数："))
    print(num**2)
except NameError:
    print("输入错误，请重新输入一个数")
```

结果 ：

```python
请输入一个数：no
输入错误，请重新输入一个数
```

### get()函数

语法 ：

```python
dict.get(key, default=None)

key -- 字典中要查找的键。
default -- 如果指定键的值不存在时，返回该默认值。
```

代码 ：

```python
dict={"a":"1","b":"2"}
x=dict.get("a","不存在")
y=dict.get("c","不存在")
print(x)
print(y)
```

结果 ：

```python
1
不存在
```



### 组合数据类型的简单总结
1. 元组是一种序列类型，**一旦创建就不能被修改**，**使用小括号 () 或 tuple() 创建，元素间用逗号分隔**

2. 列表是一种序列类型，**创建后可以随意被修改，使用方括号 [] 或list() 创建**，元素间用逗号 , 分隔，**列表中各元素类型可以不同，无长度限制**

3. 字典是键值对的集合，**键值对之间有顺序且不能重复**，采**用大括号{}和dict()创建**。

4. **集合是多个元素的无序组合，集合元素之间无序，不存在相同元素，元素间用逗号分隔，建立集合类型用 {} 或 set()，但是建立空集合类型，必须使用set()**

5. **集合可以用于数据去重**，所以如果你定义了一个列表，想要去除相同元素，可以转换为集合类型后再转换为列表即可。

代码演示 ： 集合去重

```python
L=[1,9,5,6,4,3,5,1,2,1,5,3]
L=set(L)  #列表转换为集合可以去重
L=list(L)  #去重完后可以在转换回来成列表
print(L)
```

结果 :

```python
[1, 2, 3, 4, 5, 6, 9]
```



### lambda函数

```python
a=lambda x,y:x+y
print(a(3,2))
```

结果 ：

```python
5
```

这算是lambda函数简单的用法，以这个实例先来讲一下其语法格式

```python
   lambda [arg1 [,arg2,.....argn]]:expression
# [arg…] 是参数列表
# expression 是一个参数表达式
# 冒号前是参数，可以有多个，参数之间用逗号隔开，冒号右边为表达式
```

lambda函数是一个匿名函数，为什么叫它匿名函数？

那是**因为匿名函数并不需要用def关键字来声明**，它主要应用于简单函数，不想单独去创建普通函数的时候使用

**注意：**

1. 参数表达式中的表达式不能超过一个

2. lambda 函数不能包含命令

3. lambda 函数不能访问自己参数列表之外的参数，只能完成非常简单的功能

4. 表达式中含有的参数需要在[arg…] 中有定义

### 函数sort()

**1**、仅对列表进行排序，改变列表自身顺序，无返回值。

**2、语法格式：**

```python
  list.sort(key=None, reverse=False)
  
# key：设置排序方法或者可以指定列表中用于排序的元素
# reverse：True反序，False正序，若不赋值则默认为升序排列
```

* **先对简单列表进行排序**：

  * ```python
    >>> list=[2,1,6,5,9,8,6,3,]
    >>> list.sort()
    >>> print(list)
    [1, 2, 3, 5, 6, 6, 8, 9]
    >>> list.sort(key=None,reverse= True)
    >>> print(list)
    [9, 8, 6, 6, 5, 3, 2, 1]
    ```
  
* **对字典组成的列表排序**

  * ```python
    a = [{'Mike': 99}, {'John': 98},{'zoom':96}]
    a.sort(key=lambda x: list(x.values()))
    print(a)
    
    ```

  * ```python
    [{'zoom': 96}, {'John': 98}, {'Mike': 99}]
    
    ```


**对 a.sort(key=lambda x: list(x.values())) 的理解：**
这语句中X是列表项即列表中的每个字典，list(x.values())是取字典的值转化为列表。简单讲就是用列表中每个字典的值进行排序。简单说一下：

1. d.values()	返回字典d中所有的值信息
2. d.keys()	返回字典d中所有的键信息

**（字典的值就是99，98，96，字典的键是Mike，Zoom，John）**

* 同理可推，若想要按照**名字排序**的话，可以这样写：

  * ```python
    a = [{'Mike': 99}, {'John': 98},{'zoom':96}]
    a.sort(key=lambda x: list(x.keys()))
    print(a)
    ```

  * ```python
    [{'John': 98}, {'Mike': 99}, {'zoom': 96}]
    ```

    


