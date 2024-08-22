# Python学习

[TOC]



##### 1.     错题巩固：

###### 1.     类中要使用类成员别忘了加上self.

 ![72310180656](.\md图\类成员self.png)

否则会报错

###### 2.json是字符串

###### 3.解码and编码json

解码：json字符串===(json.loads(x))===>dict字典

```python
>>> import json
>>> jsonstring = '{"name": "erik", "age": 38, "married": true}'
>>> person = json.loads(jsonstring)
>>> print(person['name'], 'is', person['age'], 'years old')
erik is 38 years old
>>> print(person)
{'name': 'erik', 'age': 38, 'married': True}
>>> type(person)
<class 'dict'>
```

编码：dict字典===(json.dumps(x))===>json字符串

```python
import json
person = {'name': 'erik', 'age': 38, 'married': True}
json_string = json.dumps(person)
print(json_string)
# {"name": "erik", "age": 38, "married": true}
# To make sure, let's print the type too
print(type(json_string))
# <class 'str'>
```

###### 4.print函数

- Python 的 print 是通过输入其名称后跟括号来调用的。

- 可选参数列在括号之间，用逗号分隔。

  ```python
  print('This is my age:', 39)
  ```

- 您可以打印数字和[字符串](https://python.land/introduction-to-python/strings)。事实上，Python 中的大多数[数据类型](https://python.land/python-data-types)都可以打印。

- 您可以混合使用参数类型，例如数字和字符串。

- 在其最基本的形式中，我们可以在没有任何参数的情况下调用 print。在这种情况下，它会打印一个空的新行。

- 该函数会将特殊字符转换为有意义的东西。例如，换行符变为实际换行符，制表符将转换为实际制表符。`print()``\n``\t`

- print（） 不会像 REPL 那样对字符串进行转义，因为我们不想向软件的用户显示转义字符串。这只是 REPL 为我们这些程序员提供的便利。

###### 5.python版本不建议太高

可以选择python3.8.10

###### 6.切片

例子：

```python
>>> range(0, 5)[2:4]
range(2, 4)
>>> range(0, 5)[4:2:-1]
range(4, 2, -1)
>>> range(0, 10)[2:8:2]
range(2, 8, 2)
```



------

##### 2.学习内容收获：

###### important：pip清华源下载

pip install some-package **-i https://pypi.tuna.tsinghua.edu.cn/simple**

###### 1.range语句功能

 ![72310119149](.\md图\range功能.png)

注意：range是圆括号()；切片是方括号[]，例如[0:8:1]：0-8的切片且步长为1

###### 2.有关字典中的keys内容

![72310125286](.\md图\keys内容.png)

###### 3.排序

包括两种：（1）带函数形式的排序（2）容器的排序

（1）

![72310127174](.\md图\列表sort.png)

（2）

 ![72310129342](.\md图\容器排序.png)

例如：

```python
  sorted_year = sorted(data_dict.keys())
```

其中dta_dict是

```python
# { 年份: [ [国家, gdp],[国家,gdp], ...... ], 年份: [ [国家, gdp], [国家,gdp], ......  ], ...... }
# { 1960: [ [美国, 123], [中国,321], ......  ], 1961: [ [美国, 123], [中国,321], ......  ], ...... }
```

中的年份。排序的目的是得到排好序的年份。

###### 4.快捷键

 ![72310132138](.\md图\快捷键.png)

Alt+回车键可以自动搜索并导包

按Alt，点击一列中的要修改的相同位置，然后松开Alt，按shift+->（向右键）开始修改

###### 5.面向对象内置方法

| 方法     | 功能                                           |
| -------- | ---------------------------------------------- |
| __init__ | 构造方法，可用于创建类对象的时候设置初始化行为 |
| __str__  | 用于实现类对象转字符串的行为                   |
| __lt__   | 用于2个类对象进行小于或大于比较                |
| __le__   | 用于2个类对象进行小于等于或大于等于比较        |
| __eq__   | 用于2个类对象进行相等比较                      |

5.pass关键字

pass是占位语句，用来保证函数（方法）或类定义的完整性，表示无内容，空的意思

例如：

```
class MyPhone(Phone, NFCReader, RemoteControl):
	pass
```

###### 6.继承中的小细节

多继承中，如果父类有同名方法或属性，**先继承的优先级高于后继承**

例如：

```
class MyPhone(Phone, NFCReader, RemoteControl):
	pass
```

若有同名方法，则优先使用Phone中的方法

###### 7.枚举函数enumerate()

参考链接：[Python中超好用的“枚举函数”：enumerate](https://mp.weixin.qq.com/s?__biz=MzAxMjUyNDQ5OA==&mid=2653572696&idx=3&sn=4d6306062e46abf786386bf5fac5bcc6&chksm=806e60e5b719e9f35e6b8681b1bfa373daac5cc2c7f54d48af2b7dd2a628f770162a69824f02&scene=27)

基本用法上，enumerate()函数可以遍历列表、元组或字符串等可迭代对象，并返回每个元素的索引和值。例如：

```python
numbers = ‌:ml-citation{ref="1,2"data="citationList"}
for index, value in enumerate(numbers):
print(index, value)
```

```python
name = ["张三","李四","王五"]
lis = [13,22,43]
for index,value in enumerate(lis):
	if value >= 18:
		print(index,name[index],value)
```

但是有时候，我们就想让第一个元素的下标变为1，第二个元素的下标变为2，怎么办呢？

 ![72310140789](.\md图\枚举函数中start.png)

从上图可以看出：enumerate()函数中有一个**start**参数，很好的帮我们解决了上述问题。

###### 8.判断是否是只由数字组成

使用str.isdigit()方法

这是最直接的方法，用于判断字符串是否只由数字组成。如果你在处理的是单个字符，这个方法同样有效。

```python
char = '5'  
if char.isdigit():  
      print(f"'{char}' 是数字")  
else:  
      print(f"'{char}' 不是数字")
```

###### 9.利用f""输出大括号

重复大括号

例如

```python
greeting = "hello"  
print(f"{{{greeting}}}")
```

得出

```
{hello}
```

###### 10.数据容器对比总结

|          | 元组                               | 列表列表                         | 字符串             | 集合                   | 字典                                               |
| -------- | ---------------------------------- | -------------------------------- | ------------------ | ---------------------- | -------------------------------------------------- |
| 元素数量 | 支持多个                           | 支持多个                         | 支持多个           | 支持多个               | 支持多个                                           |
| 元素类型 | 任意                               | 任意                             | 仅字符             | 任意                   | Key：Value  Key：除字典外任意类型  Value：任意类型 |
| 下标索引 | 支持                               | 支持                             | 支持               | 不支持                 | 不支持                                             |
| 重复元素 | 支持                               | 支持                             | 支持               | 不支持                 | 不支持                                             |
| 可修改性 | 不支持                             | 支持                             | 不支持             | 支持                   | 支持                                               |
| 数据有序 | 是                                 | 是                               | 是                 | 否                     | 否                                                 |
| 使用场景 | 不可修改、可重复的一批数据记录场景 | 可修改、可重复的一批数据记录场景 | 一串字符的记录场景 | 不可重复的数据记录场景 | 以Key检索Value的数据记录场景                       |
| 形式     | ()                                 | []                               | ""                 | {}                     | {:,}                                               |

###### 11.闭包

需要使用**nonlocal**关键字修饰外部函数的变量，才能在内部函数中修改它。

**附：**就像要使用**global**关键字在函数内部修饰变量才能更改全局变量的值

###### 12.装饰器

利用闭包来达到装饰器作用

作用：在不更改原有代码的基础上添加功能

例子：

```python
# 装饰器的快捷写法（语法糖）
def outer(func):
    def inner():
        print("我睡觉了")
        func()
        print("我起床了")

    return inner


@outer
def sleep():
    import random
    import time
    print("睡眠中......")
    time.sleep(random.randint(1, 5))


sleep()
```

在想添加功能的函数上面添加@outer，其中outer是闭包函数

其底层逻辑如下：

```python
# 装饰器的一般写法（闭包）
def outer(func):
    def inner():
        print("我睡觉了")
        func()
        print("我起床了")

    return inner


def sleep():
    import random
    import time
    print("睡眠中......")
    time.sleep(random.randint(1, 5))


fn = outer(sleep)
fn()
```

###### 13.设计模式——单例模式

实现模式：

str_tools_py.py     在该文件中定义代码

```python
class StrTools:
    pass

str_tool = StrTools()
```

test.py                    在另一个文件导入对象

```python
from str_tools_py import str_tool

s1 = str_tool
s2 = str_tool

print(id(s1))
print(id(s2))
```

test.py结果为：s1和s2是同一个对象

```python
2786600591472
2786600591472
```

###### 14.设计模式——工厂模式

```python
class Person:
    pass

class Worker(Person):
    pass

class Student(Person):
    pass

class Teacher(Person):
    pass


class PersonFactory:
    def get_person(self, p_type):
        if p_type == 'w':
            return Worker()
        elif p_type == 's':
            return Student()
        else:
            return Teacher()


pf = PersonFactory()
worker = pf.get_person('w')
stu = pf.get_person('s')
teacher = pf.get_person('t')
```

优点：

1.大批量创建对象的时候有统一的入口，易于代码维护

2.当发生修改，仅修改工厂类的创建方法即可

------

##### 3.与mysql结合

###### 1.使MySQL显示的内容转移到终端面板上

```python
# 获取所有结果
results = cursor.fetchall()

# 遍历并打印结果
for row in results:
    print(row)
```

例如：

```python
from pymysql import Connection

# 构建到MySQL数据库的链接
conn = Connection(
    host="localhost",   # 主机名（IP）
    port=3306,          # 端口
    user="root",        # 账户
    password="123456",  # 密码
    autocommit=True     # 设置自动提交
)

# print(conn.get_server_info())
# 执行非查询性质SQL
cursor = conn.cursor()      # 获取到游标对象
# 选择数据库
conn.select_db("world")
# 执行sql
cursor.execute("show tables")
# cursor.execute("create table test(id int)")
# cursor.execute("insert into student values(10001, '周杰轮', 31, '男')")

# 获取所有结果
results = cursor.fetchall()

# 遍历并打印结果
for row in results:
    print(row)

# 关闭链接
conn.close()
```

------

##### 4.与pyspark有关

###### 1.KV型RDD

KV型RDD存储的数据是二元元组

二元元组意思是数据只有两个

###### 2.算子总结

| 算子        | 功能                                                         | 备注                                                         |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| map         | 传入函数，计算数据                                           | 例如：每个数据乘以10                                         |
| flatmap     | 跟map相比，增加了去掉一个嵌套的功能                          | 例如：["a b j","i k h"]=>["a b j i k h"]                     |
| reduceByKey | 函数传入参数有两个。对相同的前数，据根据传入的函数来对后数据进行计算 | 例如：[('男',99),('女',90),('男',78),('女',89)]，设计函数获得男女生两组的成绩之和 |

| 算子     | 功能 | 备注                                                   |
| -------- | ---- | ------------------------------------------------------ |
| filter   | 过滤 | 例如：只要数据中的偶数                                 |
| distinct | 去重 |                                                        |
| sortBy   | 排序 | 有三个传入参数：排序的选择对象、升序还是降序、分布式=1 |

###### 3.reduceByKey

![72407998789](C:\Users\86150\AppData\Local\Temp\1724079987892.png)

###### 4.数据输出（RDD==>python对象）

•collect：将RDD内容转换为list

•reduce：对RDD内容进行自定义聚合

•take：取出RDD的前N个元素组成list

•count：统计RDD元素个数

###### 5.map算子简洁用法

类似的map算子链式调用连用时可以选择将这些map算子缩写在第一个map算子的函数里面

==>多个map算子连用可以缩写为一个

例如：

```python
rdd1 = txt_rdd\
    .map(lambda x: x.split("\t")[0].split(":")[0])\
    .map(lambda x: (x, 1))
```

==>（其中(x,1)放入第一个map算子里面了）

```python
rdd1 = txt_rdd\
    .map(lambda x: (x.split("\t")[0].split(":")[0], 1))
```

###### 6.将数据转换为JSON格式，写出为文件

在此过程中，用不上json.dumps(x)这个函数，因为输出到文件==>变成字符串。而json本质上就是字符串。

例子：

可以这样写：

```python
# 4.2 写出为文件
file_rdd.map(lambda x: x.split("\t")).\
    map(lambda x: {"time": x[0],
                   "user_id": x[1],
                   "key_word": x[2],
                   "rank1": x[3],
                   "rank2": x[4],
                   "url": x[5]}).\
    saveAsTextFile("D:/output_json")
```

而不必这样写：

```python
# 将数据转换为JSON格式，写出为文件
json_rdd = txt_rdd\
    .map(lambda x: x.split("\t"))\
    .map(lambda x: {"time": x[0],
                    "user_id": x[1],
                    "key_words": x[2],
                    "range1": x[3],
                    "range2": x[4],
                    "url": x[5]})\
    .map(lambda x: json.dumps(x))
json_rdd.saveAsTextFile("./output_test")
```

没必要多json.dumps(x)这一步

------

##### 5.与VScode有关

###### 1.启用自动补全和智能提示

默认情况下，VSCode 的自动补全和智能提示功能是启用的。如果没有启用，你可以通过按下 **Ctrl + Space** 来手动触发自动补全。智能提示则会在你输入代码时自动显示。

###### 2.常用的快捷键

下面是一些常用的快捷键：

Ctrl+Space：自动补全导入语句
Ctrl+. (英文句点)：快速导入包或模块
Ctrl+/：注释或取消注释一行代码

------

##### 6.与pycharm有关

###### 1.启用自动补全

快捷键：ctrl+P

###### 2.快速导入包

快捷键：Alt+Enter