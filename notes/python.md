### 基础语法

type() #查看数据的类型

```python
int(X) #转化为整数
float(x) #转化为浮点数
str(x) #转化为字符串
```

变量交换

```python
c1 = '可乐'
c2 = '牛奶'

# 使用临时变量 第一种
temp = c1
c1 = c2
c2 = temp

# 或者使用多重赋值 第二种
c1, c2 = c2, c1

# 现在c1变量的值为'牛奶'，c2变量的值为'可乐'
```

7种数据类型

```python
age = 600 #整数
height = 1.85 #浮点数
name = "孙悟空" #字符串
skills = ["筋斗云", "72变"] #列表list
achievements = ("大闹天宫",) #元组，元组不可变
#字典：用于存储键值对
abilities = {"姓名": "孙悟空", "年龄": 600, "技能": ["筋斗云", "72变"], "主要战绩": "大闹天宫"}
#集合
unique_skills = {"筋斗云", "72变"}

```

```python
#字符串的拼接
# + 号
name = '王焕然'
print("你好" +  name + ",欢迎来到湖南工商大学")
#占位符
%表示占位，s,d,f分别表示字符串，整数，浮点数
message = "我今年%d岁，家住%s"%(22,"湖南")
print(message)
# ,
str1 = "Hello"
str2 = "World"
print(str1, str2) #输出 Hello World
#fstrings
#在字符串前面加上 f 或 F，然后使用花括号 {} 来包含变量名
name = "Alice"
age = 30
message = f"My name is {name} and I am {age} years old."
print(message)
#str.format()
name = "Charlie"
age = 35
message = "My name is {} and I am {} years old.".format(name, age)
print(message)
```

### 判断语句

```python
if 判断条件:
    条件成立时，要做的事
else:
    条件不成立时，要做的事
#
if   条件:
    
elif 条件:

else:
    
```

### 循环

```python
i=0
while i<100:
    循环语句
```

```python
for 临时变量 in 待处理数据集:
	循环满足条件时执行的代码
for 变量 in 可迭代对象:#可迭代对象有字符串、列表、元组等
    # 循环体
for i in range(1,10):
    print(i)
#range(start,stop)输出从start到stop-1
#range() 函数返回的对象是一个可迭代的序列，通常与 for 循环一起使用，可以使用 list() 函数将其转换为列表，以查看其内容。
my_range = range(3, 10, 2)
my_list = list(my_range)
print(my_list)  # 输出：[3, 5, 7, 9]、
```

### 列表

#### 列表定义

```python
变量名称 = [1,2,3,4,...]
#定义空列表
变量名臣 = []
变量名称 = list()
```

#### 列表索引

```python
name_list = ['tom','lily','rose',['lihua','liming']]
print(name_list[0]) #左往右从零开始,tom
print(name_list[-1]) #右往左从-1开始,['lihua','liming']
print(name_list[3][1]#liming
```

#### 列表操作

```python
#查询列表下标:列表.index(元素)
my_List = ['lihua','aming','python']
print(my_list.index('python'))
#修改下标值
my_List[1]='zisui'
print(my_List[1])
#指定位置插入元素 列表.insert(下标,元素)
my_List.insert(1,'moran')
#追加元素 列表.append(元素) 一次只能追加一个元素,一个数据容器也是一个数据
my_List.append([1,2,3]) #['lihua', 'zisui', 'python', [1, 2, 3]]
#追加元素2 列表.extend(其他数据容器)
my_List.extend([2,3,4])
#删除元素 语法：del 列表[下标] / 列表.pop(下标)
del my_List[1]
my_List.pop(1)
#删除某元素在列表中的第一个匹配项
my_List.remove(2) #仅仅是第一个
#清空列表内容
my_List.clear()
#统计某元素在列表中的数量
my_List.count(1)
#统计列表内有多少元素
len(my_List)
#列表的合并
list1 = [1, 2, 3]
list2 = [4, 5, 6]
merged_list = list1 + list2 # + 号
print(merged_list) 
list1.append(list2) # append()方法
print(list1)
```

![{9553C971-C09D-4780-94CF-974C629A829F}](D:\Typora\notes\python.assets\{9553C971-C09D-4780-94CF-974C629A829F}.png)

#### 列表的循环

```python
#包括两种，一个是while循环，一个是for迭代
i=0
while 循环条件:
    循环语句
for 变量 in 可迭代对象:#可迭代对象有字符串、列表、元组等
    # 循环体
index = 0
while index < len(列表):
    元素 = 列表[index]
    对元素进行处理
    index += 1
for i in my_List:
    print(i)
while循环和for循环，都是循环语句，但细节不同：
在循环控制上：
while循环可以自定循环条件，并自行控制
for循环不可以自定循环条件，只可以一个个从容器内取出数据
在无限循环上：
while循环可以通过条件控制做到无限循环
for循环理论上不可以，因为被遍历的容器容量不是无限的
在使用场景上：
while循环适用于任何想要循环的场景
for循环适用于，遍历数据容器的场景或简单的固定次数循环场景
```

### 元组

```python
#元组的定义
变量名 = (元素，元素，元素,....)
#定义空元组
变量名 = ()
变量名 = tuple()
#同样支持嵌套
#元组的操作
元组.index(元素)#查找元素下标
元组.count(元素)#统计元素在列表中的个数
len(元组)
#创建单个元素的元组时，需要在元素后面加上逗号，以区分它与普通括号。
```

### 字符串

```python
#字符串的替换
name = 'good'
name_new = name.replace('g','r')
#.replace('原元素'，'现元素')
#字符串的分离 .split(分割元素)得到一个列表
#字符串的规整操作 字符串.strip(前后去除字符串)
```

![{C57D9D85-3313-437e-BFAF-8F222CB507D9}](D:\Typora\notes\python.assets\{C57D9D85-3313-437e-BFAF-8F222CB507D9}.png)

### 序列

序列是指：内容连续、有序，可使用下标索引的一类数据容器列表、元组、字符串，均可以可以视为序列。

语法：序列[起始下标:结束下标:步长]

```python
my_list = [1, 2, 3, 4, 5]
new_list = my_list[1:4]	# 下标1开始，下标4（不含）结束，步长1
print(new_list)		# 结果：[2, 3, 4]
```

### 集合

集合无序，所以不支持下标索引访问

和列表一样支持修改

不支持while循环

![{41B11D6A-997B-4c03-B3E1-8508B4359E4E}](D:\Typora\notes\python.assets\{41B11D6A-997B-4c03-B3E1-8508B4359E4E}.png)

### 字典

同集合一样不能使用下标索引

键值对：key:value

value可以为任意数据类型，key不能为字典

![{33B567F1-CCCA-4522-AD6A-78058975CD3C}](D:\Typora\notes\python.assets\{33B567F1-CCCA-4522-AD6A-78058975CD3C}.png)

![{5DEB9160-201A-4fc4-AED8-51B4BABCF5A1}](D:\Typora\notes\python.assets\{5DEB9160-201A-4fc4-AED8-51B4BABCF5A1}.png)

### 函数

```python
#函数结构
def function_name(parameters):
    # 函数体
    # 执行操作
    return result  # 可选
```

### 文件

open()打开函数

```python
open(name,mode,encoding)
f = open('python.txt','r',UTF-8)
mode有三种方式
r为只读
w为创建并写入或者写入，原有内容会被删除
a为追加内容

read()方法
文件对象.read(num) #num为传入数据长度（字节）
readLines() #按照行读取，放回的是列表
for line in open('python.txt','r')
	print(line)
close() #关闭文件
with open() as f:
    #自动关闭

f = open('python.txt','w')
f.write('hello')
f.flush() #内容刷新，一次将缓存区的文件全部写入到磁盘
```

### 输出

```python
# 创建一个列表
my_list = [1, 2, 3, 4, 5]

# 使用for循环遍历列表元素
for item in my_list:
    print(item)
# 输出:
# 1
# 2
# 3
# 4
# 5
```

```python
# 创建一个元组
my_tuple = (1, 2, 3, 4, 5)

# 使用for循环遍历元组元素
for item in my_tuple:
    print(item)
# 输出:
# 1
# 2
# 3
# 4
# 5
```

```python
# 创建一个字符串
my_string = "Hello, World!"

# 使用for循环遍历字符串中的字符
for char in my_string:
    print(char)
# 输出:
# H
# e
# l
# l
# o
# ,
#  (空格)
# W
# o
# r
# l
# d
# !
```

```python
# 创建一个字典
my_dict = {'name': 'Alice', 'age': 30, 'city': 'New York'}

# 使用for循环遍历字典的键
for key in my_dict:
    print(key)
# 输出:
# name
# age
# city

# 使用for循环遍历字典的值
for value in my_dict.values():
    print(value)
# 输出:
# Alice
# 30
# New York

# 使用for循环遍历字典的键值对
for key, value in my_dict.items():
    print(key, ":", value)
# 输出:
# name : Alice
# age : 30
# city : New York
```

### 异常

```python
try:
    可能发生错误的代码
except:
    如果出现异常执行的代码
```

### 模块

```python
import 模块名
from 模块名 import 类、变量、方法等
from 模块名 import * #导入全部模块
import 模块名 as 别名
from 模块名 import 功能名 as 别名
```

```python
__all__ = ['variable1', 'function1', '模块名'] #指定哪些模块可以被from 模块名 import *
```

### 列表推导式

```python
基本语法：
new_list = [expression for item in iterable if condition]
解释：
new_list：要创建的新列表的名称。
expression：用于对每个 item 进行操作以生成新元素的表达式。
item：可迭代对象中的每个元素。
iterable：可迭代对象，例如列表、字符串、元组等。
condition（可选）：一个条件表达式，用于过滤元素。
```

### def class self

1. `def`：`def` 是 Python 中用于定义函数（方法）的关键字。函数是一段可重用的代码块，可以接受参数并执行特定的任务。在类中，`def` 用于定义类的方法，这些方法是类的行为，可以在类的实例上调用。

   例如，下面是一个简单的类定义，其中包含一个方法：

   ```
   pythonCopy codeclass MyClass:
       def my_method(self, arg1, arg2):
           # 方法的定义
           # 可以在这里执行特定的任务
   ```

2. `class`：`class` 是 Python 中用于定义类的关键字。类是一种自定义数据类型，它可以包含属性和方法。属性是类的数据成员，方法是类的函数成员。类可以用来创建对象（类的实例）。

   在类中，`self` 是一个特殊的参数，它表示类的实例本身。`self` 在方法定义中作为第一个参数，用于引用类的实例的属性和方法。通过 `self`，你可以在方法内部访问和修改对象的状态。

   例如，上面的示例中的 `my_method` 中的 `self` 参数允许你访问类的属性和调用其他方法：

   ```
   pythonCopy codeclass MyClass:
       def __init__(self, x):
           self.x = x
   
       def my_method(self, arg1, arg2):
           result = self.x + arg1 + arg2
           return result
   ```

   在创建类的实例后，你可以使用 `self` 来访问实例的属性：

   ```
   pythonCopy codeobj = MyClass(10)
   result = obj.my_method(5, 3)  # 这里的 self 将指向 obj 实例
   ```

总之，`def` 用于定义函数和类的方法，`class` 用于定义类，而 `self` 是在类中方法中用于引用类的实例的特殊参数。这三个概念结合在一起，允许你创建面向对象的代码，定义类和方法，以及操作类的实例。
