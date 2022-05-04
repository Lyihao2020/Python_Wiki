# 第六讲 : 用户输入与循环语句

[TOC]

### range()函数

ange()函数也是Py的一个内置函数，它的作用是生成一系列的整数，其语法格式如下：
```
range(start,end,step)
```
* start：计数起始值，省略则从0开始。
* end：计数结束值(不包括本值)，如range(3)表示0~2，不可省略！
* step：步长。
**重点： 使用range()函数时，如果只有一个参数，那么表示指定的是 end值，如果是两个参数，则表示的是start和end，只有三个参数都在时步长才可以表示出来。**

## For语句

### 计数循环遍历

```python
for<循环变量> in <遍历结构>：
    <语句块>
  
# 解释：
1、从遍历结构中逐一提取元素，放在循环变量中
2、每次循环，所获得元素放入循环变量，并执行一次语句块
```

代码演示 :

```python
for i in range(5):   #计数循环，遍历有range()函数产生的数字序列，产生循环
    print("加油:",i)
print("===============")
for i in range(1,8,2):
    print("加油：",i)
```

结果 :

```python
加油: 0
加油: 1
加油: 2
加油: 3
加油: 4
===============
加油： 1
加油： 3
加油： 5
加油： 7
```

### 字符串循环遍历

```python
for c in s :
    <语句块>
# s是字符串，遍历字符串每个字符，产生循环
```

代码演示 ：

```python
>>> s="abcd123"
>>> for c in s:
 print(c)
```

结果 :

```python
a
b
c
d
1
2
3
```

### 列表遍历循环

```python
for item in ls : 
    <语句块> 
# ls是一个列表，遍历其每个元素，产生循环
```

代码演示 :

```python
>>> for item in [12,"aa",33]:
 print(item)
```

结果 :

```python
12
aa
33
```

### 文件遍历循环

```python
for line in fi : 
     <语句块> 
# fi是一个文件标识符，遍历其每行，产生循环
```

### for循环的扩展模式

```python
for <循环变量> in <遍历结构>:
    <语句块1>
else:
    <语句块2>

# 注意：
当for循环正常执行之后，程序会继续执行else语句中的内容。else语句只在循环正常执行并结束后才执行。
```



## While循环

### 循环格式 :
```python
while <条件> : 
    <语句块> 
```

反复执行语句块，直到条件不满足时结束

### while循环的扩展模式

```
while <条件>:
    <语句块1>
else:
    <语句块2>
1234
```

注意：当while循环正常执行后，程序会继续执行else语句中的内容。else语句只在循环正常执行后才执行，因此，可以在语句块2中放置判断循环执行情况的语句。

## 循环控制保留字

### break语句
break用来跳出最内层for或while循环，脱离该循环后程序从循环代码后继续执行。
注意：若有双重循环时，仅退出当前层次循环

代码：

```python
for s in "abcd":
    for i in range(10):
        print(s,end="") # 输出在同一行
        if s=="b": 
            break
```
结果：
```python
aaaaaaaaaabccccccccccdddddddddd
```

### continue语句
用来结束当前当次循环，即跳出循环体中下面尚未执行的语句，但不跳出当前循环。

代码：
```python
for s in "abcd":
    if s=="b":
        continue
    print(s,end="")
```
结果：
```python
acd
```

### 比较

e.g 1

```python
for s in "abcd":
    if s=="b":
        break
    print(s,end="")
```
结果：
```
a
```
e.g 2
```python
for s in "abcd":
    if s=="b":
        continue
    print(s,end="")
```
结果：
```
acd
```
