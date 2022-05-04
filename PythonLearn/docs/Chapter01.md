# 第一讲 ：基本介绍、变量与简单数据类型

[TOC]



### 基本函数介绍

Python中存在一些系统内置的函数，例如 print

```python
>>> print("Hello World!")
Hello World!
```

而通过 dir(_ __ builtins_ _  _) 可以查询Python中的基本内置函数与符号

```python
>>> dir(__builtins__)
['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'ZeroDivisionError', '__build_class__', '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']
```



### 引入 ：设计第一个游戏

```python
"""用Python设计第一个游戏"""
# input输入信息
temp = input("不妨猜一下我心里现在在想那个数字")
guess = int(temp) # 类型转换

if guess == 0 : # 这里是python的条件分支语句
    print("猜中啦！") # 打印相关信息
else:
    print("很遗憾哦，心里想的是0")

print("游戏结束，不玩了")
```



## 变量

```python
>>> x = 3
>>> y = 6
>>> print(x,y)
3 6
>>> 幸运数 = 100 #中文也可以做变量名
>>> print(幸运数)
100
```

当涉及到中文时 ， 就要考虑 中文变量名与字符串

当文本中出现了不可避免的单引号，就要使用双引号来避免

```python
>>> print('I love China')
I love China

>>> print("I love English")
I love English

>>> print('Let's go!')
SyntaxError: invalid syntax
          
>>> print('"Let's go!"')
SyntaxError: invalid syntax
          
>>> print('"Let/'s go!"')
SyntaxError: invalid syntax
          
>>> print('"Let\'s go!"') #使用转义字符
"Let's go!"
```

![截屏2022-05-04 08.42.07](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205040842590.png)

```python
>>> print("D:\three\two\one\none")	  
D:	hree	wo\one
one

>>> print("D:\\three\\two\\one\\none")  
D:\three\two\one\none
  
>>> print(r"D:\three\two\one\none") #加r说明为原始字符串
D:\three\two\one\none
```

**使用反斜杠要注意，就不能把它放在末尾，因为放在末尾，说明这个字符串还没完**

**Python中的回车换行，是有语法含义的，能隔断语义**

### 整数类型

1. 与数学中的整数概念一致，没有取值范围限制。

2. 整数类型共有4种进制表示：十进制、二进制、八进制、
   十六进制，默认十进制，其他进制需增加引导符（不区分
   大小写）
   1. 二进制 0b或0B，例：0b1010，0B1010
   2. 八进制 0o或0O，例：0o1010, 0O1010
   3. 十六进制 0x或0X，例：0x1010, 0X1010
     

### 浮点数类型

1. 浮点数类型与数学中实数的概念一致，表示带有小数的
数值。必须有小数部分，小数部分可以是0。

2. 浮点数有2种表示方法：
	1. 十进制：10.0
	2. 科学计数法：e**=a\*10^b**
```python 
例如：  1.01e3
			-1.10E-3
```

### 复数类型

1. Python语言中，复数可以看做是二元有序实数对(a,b)，
   表示a+bj，其中，a是实数部分，b是虚数部分。

2. z = 1.23e-4+5.6e+89j
   对于复数z，可以用z.real获得实数部分，z.imag获得
   虚数部分

## 数值类型的运算

### 数值运算操作符

![截屏2022-05-04 09.36.13](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205040936967.png)

### 数值运算函数

![截屏2022-05-04 09.36.26](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205040936279.png)

### 基本运算

* 整数和浮点数混合运算，输出结果是浮点数

  * ```python
    >>>1010.0//3 #浮点数与整数运算，产生结果是浮点数
    336.0
    ```
  
* 整数之间运算，产生结果类型与操作符相关，除法运算（/）的结果是浮点数；
	* ```python
		>>>1010/10 #/运算的结果是浮点数
		101.0
		```
	
* 整数或浮点数与复数运算，输出结果是复数

  * ```python
    >>>10-(1+1j) #等价于(10-1)-2j
    (9-1j)
    ```

## 字符串类型

### 字符串类型介绍

1. 根据字符串的内容多少分为单行字符串和多行字符串。

2. 单行字符串可以由一对单引号（’）或双引号（"）作为边
   界来表示，单引号和双引号作用相同。

3. 多行字符串可以由一对三单引号（’’’）或三双引号（"""）
   作为边界来表示，两者作用相同。

### 转义字符

**反斜杠字符（\）是一个特殊字符**，在Python字符串中
表示“转义”，即该字符与后面相邻的一个字符共同组成了
新的含义。
例如：

```python
\n表示换行
\\表示反斜杠
\'表示单引号
\"表示双引号
\t表示制表符（Tab）等。
```

### 字符串中的序号

![截屏2022-05-04 12.58.43](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041258248.png)

因为字符串有规定序号，所以可以像数组一样索引

### 字符串的索引

对字符串中某个字符的检索称为索引。格式如下：

```python
<字符串或字符串变量>[序号]
```

代码演示：

```python
>>> s="关关雎鸠，在河之洲。"
>>> s[5]
'在
```

### 字符串的切片
对字符串中某个子串或区间的检索被称为切片
格式如下：
普通用法：

```
<字符串>[M: N]，M缺失表示至开头，N缺失表示至结尾
```

代码演示：
```python
>>> s="关关雎鸠，在河之洲。"
>>> s[1:5]
>>> '关雎鸠，'
```
高级用法：
```python
<字符串>[M: N: K]，根据步长K对字符串切片
```

代码演示：

```python
>>> s="关关雎鸠，在河之洲。"
>>> s[1:6:2]
'关鸠在'
```

### 字符串操作符

| 操作符及使用   | 描述                                    |
|:--------------:|:---------------------------------------:|
| x + y          | 连接两个字符串x和y                      |
| n * x 或 x * n | 复制n次字符串x                          |
| x in s         | 如果x是s的子串，返回True，否则返回False |

代码演示：

```python
>>> s="关关雎鸠，在河之洲。"
>>> s[1:5]
'关雎鸠，'
>>> s1="窈窕淑女，君子好逑"
>>> s1+s
'窈窕淑女，君子好逑关关雎鸠，在河之洲。'
>>> s*2
'关关雎鸠，在河之洲。关关雎鸠，在河之洲。'
>>> s1 in s
False
```

### Str()函数的使用

1. str() 函数将对象转化为适于人阅读的形式。

2. 将整形转化为字符串形式

   ```python
   >>> a=123
   >>> str(a)
   '123'
   ```

3. 转化列表之类的元素为字符串类型

   ```python
   >>> list=["abcd","123456"]
   >>> str(list)
   "['abcd', '123456']"
   ```

### 字符串处理函数

| 函数及使用       | 描述                                  |
|:----------------:|:--------------------------------:|
| len(x)           | 长度，返回字符串x的长度               |
| str(x)           | 任意类型x所对应的字符串形式           |
| hex(x) 或 oct(x) | 整数x的十六进制或八进制小写形式字符串 |
| chr(u)           | x为Unicode编码，返回其对应的字符      |
| ord(x)           | x为字符，返回其对应的Unicode编码      |

![截屏2022-05-04 13.03.46](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041303168.png)



### 字符串处理方法

|方法及使用	|描述|
|:-----------:|:---------------:|
|str.lower() 或 str.upper()|	返回字符串的副本，全部字符小写/大写|
|str.split(sep=None)|	返回一个列表，由str根据sep被分隔的部分组成|
|str.count(sub)	|返回子串sub在str中出现的次数|
|str.replace(old, new)|	返回字符串str副本，所有old子串被替换为new|
|str.center(width[,fillchar])|	字符串str根据宽度width居中，fillchar可选|
|str.strip(chars)|	从str中去掉在其左侧和右侧chars中列出的字符|
|str.join(iter)|	在iter变量除最后元素外每个元素后增加一个str|
|str.lstrip(chars)|从str中去掉在其左侧chars中列出的字符|
|str.rstrip(chars)|从str中去掉在其右侧chars中列出的字符|

代码演示：

```python
>>> s="abc,def"
>>> s.upper()
'ABC,DEF'
>>> s.split(",")
['abc', 'def']
>>> s.count("a")
1
>>> s.replace("a","ABC")
'ABCbc,def'
>>> s.center(20,"@")
'@@@@@@abc,def@@@@@@@'
>>> s.strip("Ab")  #注意连续三个的区别
'abc,def'
>>> s.strip("a")
'bc,def'
>>> s.strip("acf")
'bc,de'
>>> ",".join(s)  #结合上面所说理解
'a,b,c,,,d,e,f'
>>> ",".join("abcd")
'a,b,c,d'

```

### 字符串类型的格式化

字符串格式化使用.format()方法，用法如下：

```python
<字符串>.format(<逗号分隔的参数>)
```

![截屏2022-05-04 13.10.08](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041310817.png)

![截屏2022-05-04 13.10.28](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041310812.png)

代码演示：

```python
print("{}爱打篮球，{}喜欢玩LOL".format("小狗","小虎"))
```

结果：

```python
小狗爱打篮球，小虎喜欢玩LOL
```

