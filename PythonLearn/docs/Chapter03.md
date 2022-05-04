# 第三讲 ：操作列表

[TOC]

## 文件的访问

```python
1:使用open（）函数打开（或建立）文件，返回一个file对象。
2：使用file对象的读/写方法对文件进行读写操作。
3：使用file对象的close（）方法关闭文件。
```

代码演示 :

```python
file=open("文本.txt",'r')
tf=file.read()
file.close()
print(tf)  
```



## 数据组织的维度

### 一维数据

1. 由对等关系的有序或无序数据构成，采用线性方式组织

2. 无论采用任何方式分割和表示，一维数据都具有线性的特点

3. 列表类型可以表达一维有序数据

#### 一维数据的表示

> **1、列表类型可以表达一维有序数据**
> 例如：ls = [3, 4, 5]
>
> **2、集合类型可以表达一维无序数据**
> 例如：st = {3., 4, 5}
>
> **3、for循环可以遍历数据，进而对每个数据进行处理**

#### 一维数据的存储

> **1、存储方式一：空格分隔**
>
> 使用一个或多个空格分隔进行存储，不换行
>
> **2、存储方式二：逗号分隔**
>
> 使用英文半角逗号分隔数据进行存储，不换行
>
> **3、存储方式三：其他方式**
>
> 使用其他符号或符号组合分隔，建议采用特殊符号

#### 一维数据的读入处理

##### 从空格分割的文件中读入数据

代码演示 :

```python
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.txt","r",encoding='utf-8')
txt=tf.read()
Is=txt.split()
print(Is)
tf.close()
```

结果 :

```python
['中国', '美国', '法国', '俄罗斯', '英国', '澳大利亚']
```

##### 从特殊符号分割的文件中读入数据

代码演示 :

```python
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.txt","r",encoding='utf-8')
txt=tf.read()
Is=txt.split("@") # 只是分隔方式发生了改变
print(Is)
tf.close()
```

结果 :

```python
['中国', '美国', '法国', '俄罗斯', '英国', '澳大利亚']
```

####一维数据的写入处理
1. 采用空格分隔方式将数据写入文件
代码演示：
```python
Is=["中国","美国","法国"]
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.txt","w")
tf.write(" ".join(Is))
tf.close()
```
2. 采用特殊分隔方式将数据写入文件
```python
Is=["中国","美国","法国"]
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.txt","w")
tf.write("@".join(Is))
tf.close()
```


### 二维数据

####二维数据的表示

1. 列表类型可以表达二维数据(使用二维列表)
例如：
```python
[ [3, 4, 5],
[6, 7, 8] ]
```
2. 使用两层for循环遍历每个元素

####CSV格式与二维数据存储

注意：每行一个一维数据，采用逗号分隔，无空行

![截屏2022-05-04 14.25.01](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041425811.png)

注意：

1. 纯文本格式，通过单一编码表示字符。
2. 以行为单位，开头不留空行，行之间没有空行
3. 每行表示一个一维数据，多行表示二维数据。
4. 以逗号（英文，半角）分割每列数据，**列数据为空也要保留逗号**
5. **对于表格数据，可以包含或不包含列名，包含时列名放置在文件第一行**

#### 二维数据的读入处理(从CSV格式的文件中读入数据)

```python
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.csv","r")
Is=[]
for line in tf:
    line = line.replace("\n","")
    Is.append(line.split(","))
print(Is)#此时Is为二维数据，所以应注意输出格式
for line in Is:
    line=",".join(line)#列表以“,”为分隔符转换成字符串传输出
    print(line)
tf.close()
```

结果 : 

![截屏2022-05-04 14.28.32](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041428152.png)

#### 二维数据的写入处理（将数据写入CSV格式的文件）

```python
Is=[["姓名","数学","英语"],["小虎","99","97"],["小红","96","98"]]#二维列表
tf=open("C:\\Users\\我的电脑\\Desktop\\文本.csv","w")
for item in Is:
    tf.write(",".join(item)+"\n")#列表item以“,”为分隔符转换成字符串写入
tf.close()
```

结果 :

![截屏2022-05-04 14.29.42](https://gitee.com/liangjie0509/MarkdownPhoto/raw/main/img/202205041429726.png)
