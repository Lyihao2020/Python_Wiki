# 第九讲 ：文件与异常

[TOC]

## 异常

**这里我们列举一些常见的程序报错：**

* ZeroDivisionError，0作为除数时的报错
* NameError 未声明变量引发的错误
* IndexError 索引超出序列范围
* IndentationError 缩进错误
* ValueError 传值错误
* KeyError 请求不存在的字典关键字
* IOError 输入输出错误
* ImportError import语句无法找到模块
* AttributeError 尝试访问未知对象属性
* TypeError 类型不合适
* MemoryError 内存不足

### try-except语句

先看下面小程序：

```python
num=eval(input("请输入一个数："))
print(num**2)
```

结果：

```python
请输入一个数：2
4
```

**如果我们输入的不是数**
结果：

```python
请输入一个数：no
Traceback (most recent call last):
  File "C:\Users\我的电脑\AppData\Local\Programs\Python样本1.py", line 1, in <module>
    num=eval(input("请输入一个数："))
  File "<string>", line 1, in <module>
NameError: name 'no' is not defined

```

可以看到，Python解释器返回了异常信息，同时推出了程序

**Python使用try-except语句来实现异常处理**，其基本语法格式如下：

```python
try:
	block1
except [ExceptionName [as alias]]:
	block2
  
  # [ExceptionName [as alias]] 是可选参数，用于指定要捕获的异常，ExceptionName则是异常名称，如果要加上as关键字，则表示为当前异常指定一个别名。
```

**raise抛出异常**
```python
raise [ExceptionName(reason)]
```
reason用于指定错误的描述信息，如果省略不写则原样抛出

**assert断言**
```python
assert expression[,reason]
```
expression为assert语句的条件表达式，如果条件为假则抛出异常，该语句很常用，通常用于检测错误位置，reason是对错误的补充描述。

代码如下：

```python
try:
    num=eval(input("请输入一个数："))
    print(num**2)
except NameError:
    print("输入错误，请重新输入一个数")
```

结果：

```python
请输入一个数：no
输入错误，请重新输入一个数
```

### try-except 高级用法

#### 用法1

语法格式 :

```python
try:
    <语句块1>
except <异常类型1>:
    <语句块2>    
...
except <异常类型N>:
    <语句块N+1>
except:
    <语句块N+2>
```

其中，第一到第N个except语句后面都指定了异常类型，说明这些except所包含的语句块只处理这些类型的异常。**最后一个except语句没有指定任何类型，表示它对应的语句块可以处理所有其他异常。**

代码如下:

```python
try:
    list=["a","b","c","d","e","f"]
    num=eval(input("请输入一个整数作为索引："))
    print(list[num])
except NameError:
    print("输入错误，请重新输入一个整数")
except:
    print("其他错误")
```

结果 :

```python
请输入一个整数作为索引：2
c

请输入一个整数作为索引：no
输入错误，请重新输入一个整数

请输入一个整数作为索引：2.3
其他错误
```

#### 用法2

语法格式：

```python
try:
    <语句块1>
except<异常类型1>:
    <语句块2>
else:
    <语句块3>
finally：
    <语句块4>
```

**解释：**

1. 此处的else语句与for循环和while循环中else一样，当try中的语句块1正常执行结束且没有发生异常时，else中的语句块3执行。

2. finall语句块则不一样，无论try中的语句块1是否发生异常，语句块4都会执行，因此将程序执行语句块1的一些收尾工作放在这里，例如：关闭、打开文件等。

