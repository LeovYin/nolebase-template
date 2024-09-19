# Python基本语法

## 编码

默认情况下，Python 3 源码文件以 **UTF-8** 编码，所有字符串都是 unicode 字符串。 当然你也可以为源码文件指定不同的编码：
```Python
# -*- coding:utf-8 -*-  #UTF-8 是最常用的编码方式，适用于大多数情况。

# -*- coding: gbk -*- #GBK 是一种用于简体中文的编码方式。
```
## 标识符

- 第一个字符必须是字母表中字母或下划线 _ 。
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。

在 Python 3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

## python保留字

保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：
```python
 import keyword
print(keyword.kwlist) 
```
输出结果：
```
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 注释

Python中单行注释以 **#** 开头，多行注释可以用多个 # 号，还有 ''' 和 """。

## 行与缩进

python最具特色的就是使用缩进来表示代码块，不需要使用大括号 {} 。

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。

## 多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用`反斜杠 \ `来实现多行语句，例如：

```python
total = item_one + \
        item_two + \
        item_three
```
在 `[]`, `{}`, 或 `()` 中的多行语句，不需要使用反斜杠 \，例如：

```python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

## 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是 Python 语法的一部分。书写时不插入空行，Python 解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：空行也是程序代码的一部分。**

## 等待用户输入

执行下面的程序在按回车键后就会等待用户输入：
```python
#!/usr/bin/python3 
input("\n\n按下 enter 键后退出。")
```

以上代码中 ，\n\n 在结果输出前会输出两个新的空行。一旦用户按下 **enter** 键时，程序将退出。

## 同一行显示多条语句

Python 可以在同一行中使用多条语句，语句之间使用分号 ; 分割，以下是一个简单的实例：


```python
#!/usr/bin/python3 
import sys; x = 'runoob'; sys.stdout.write(x + '\n')
```

使用脚本执行以上代码，输出结果为：

```
runoob
```
## 多个语句构成代码组

缩进相同的一组语句构成一个代码块，我们称之代码组。

像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。

我们将首行及后面的代码组称为一个子句(clause)。

如下实例：

```python
if expression : 
   suite
elif expression : 
   suite 
else : 
   suite
```


## import 与 from...import

在 python 用 import 或者 from...import 来导入相应的模块。

将整个模块(somemodule)导入，格式为： import somemodule

从某个模块中导入某个函数,格式为： from somemodule import somefunction

从某个模块中导入多个函数,格式为： from somemodule import firstfunc, secondfunc, thirdfunc

将某个模块中的全部函数导入，格式为： from somemodule import *

### 导入 sys 模块

```python
import sys 
print('================Python import mode==========================') 
print ('命令行参数为:') for i in sys.argv: print (i) 
print ('\n python 路径为',sys.path)
```

### 导入 sys 模块的 argv,path 成员

```python
from sys import argv,path # 导入特定的成员 
print('================python from import===================================') 
print('path:',path) # 因为已经导入path成员，所以此处引用时不需要加sys.path
```

## 命令行参数

很多程序可以执行一些操作来查看一些基本信息，Python可以使用-h参数查看各参数帮助信息：
```python
$ python -h
usage: python [option] ... [-c cmd | -m mod | file | -] [arg] ...
Options and arguments (and corresponding environment variables):
-c cmd : program passed in as string (terminates option list)
-d     : debug output from parser (also PYTHONDEBUG=x)
-E     : ignore environment variables (such as PYTHONPATH)
-h     : print this help message and exit

[ etc. ]
```
## 算术运算符
`**`    乘方
`*`      乘法
`/`      除法
`//`    地板除（整除）
`%`      取余
`+`      加法
`-`      减法
`|`      位或
`^`      移位或
`&`      位与
`<<`    左移
`>>`    右移

### 转义字符
`\n`换行符
`\t`制表符
`\r`回车
在python运算中，如果想打出原字符可以这样`print(R'\\\')`,加个`R`

# 数据类型
### 多个变量赋值

Python允许你同时为多个变量赋值。例如：

```python
a = b = c = 1
```

以上实例，创建一个整型对象，值为 1，从后向前赋值，三个变量被赋予相同的数值。

您也可以为多个对象指定多个变量。例如：

a, b, c = 1, 2, "runoob"

以上实例，两个整型对象 1 和 2 的分配给变量 a 和 b，字符串对象 "runoob" 分配给变量 c。







## 基本数据类型
在Python中，常见的基本数据类型包括整数（int）、浮点数（float）、布尔值（bool）、字符串（str）、列表（list）、元组（tuple）、集合（set）和字典（dict）。下面是这些基本数据类型的简要介绍：

1. 数字
	1. `整数（int）`：表示整数， 只有一种整数类型 int，表示为长整型比如 1, 100, -5 等。                                                                                      
	2. `二进制：0b+数字  `例如：0b101,0B101                                                                                               
	3. `八进制：0o+数字` 例如：0o24,0O24                                                           
	4. `十六进制：0x+数字 `例如：0x3F,0X3F    python默认将其他进制转换成十进制
	5. `浮点数（float）`：表示带有小数点的数，比如 3.14, 2.0, -0.5 等。
	6. `布尔值（bool）`：表示逻辑值，只有两个取值 True 和 False。
	7. `复数 (complex)` ：复数由实部和虚部组成，形式为 a + bj，其中 a 是实部，b 是虚部，j 表示虚数单位。如 1 + 2j、 1.1 + 2.2j
2. `字符串（str）`：表示文本数据，用单引号或双引号括起来，比如 'hello', "world" 等。`字符串可以进行加乘运算` `+`可以连接字符串  `*`可以让字符串重复打印，如`*3`就是把字符串打印三遍（不会换行 无间隔符）
3. `列表（list）`：表示一组有序的元素，可以包含不同类型的数据，用方括号括起来，比如 \[1, 2, 3], \['a', 'b', 'c'] 等。
4. `元组（tuple）`：类似于列表，但是元素不可变，用圆括号括起来，比如 (1, 2, 3), ('a', 'b', 'c') 等。
5. `集合（set）`：表示一组互不相同的元素，用大括号括起来，比如 {1, 2, 3}, {'a', 'b', 'c'} 等。
6. `字典（dict）`：表示键值对的集合，用大括号括起来，比如 {'name': 'Alice', 'age': 25}, {'apple': 3, 'banana': 2} 等。

## 数字(Number)
Python3 支持 **int、float、bool、complex（复数）**。
在Python 3里，只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。

像大多数语言一样，数值类型的赋值和计算都是很直观的。



## 字符串(String)

- Python 中单引号 ' 和双引号 " 使用完全相同。
- 使用三引号(''' 或 """)可以指定一个多行字符串。
- 转义符 \。
- 反斜杠可以用来转义，使用 r 可以让反斜杠不发生转义。 如 **r"this is a line with \n"** 则 \n 会显示，并不是换行。
- 按字面意义级联字符串，如 **"this " "is " "string"** 会被自动转换为 **this is string**。
- 字符串可以用 + 运算符连接在一起，用 * 运算符重复。
- Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。
- Python 中的字符串不能改变。
- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。
- 字符串切片 `str[start:end]`，其中 start（包含）是切片开始的索引，end（不包含）是切片结束的索引。
- 字符串的切片可以加上步长参数 step，语法格式如下：`str[start:end:step]`

word = '字符串'
sentence = "这是一个句子。"
paragraph = """这是一个段落，
可以由多行组成"""

### 实例(Python 3.0+)

```python
#!/usr/bin/python3 
str='123456789'

print(str) # 输出字符串
print(str[0:-1]) # 输出第一个到倒数第二个的所有字符 
print(str[0]) # 输出字符串第一个字符 
print(str[2:5]) # 输出从第三个开始到第六个的字符（不包含） 
print(str[2:]) # 输出从第三个开始后的所有字符 
print(str[1:5:2]) # 输出从第二个开始到第五个且每隔一个的字符（步长为2） 
print(str * 2) # 输出字符串两次 
print(str + '你好') # 连接字符串 
print('------------------------------') 
print('hello\nrunoob') # 使用反斜杠(\)+n转义特殊字符
print(r'hello\nrunoob') # 在字符串前面添加一个 r，表示原始字符串，不会发生转义
```

这里的 r 指 raw，即 raw string，会自动将反斜杠转义，例如：

```python
print('\n')       # 输出空行

print(r'\n')      # 输出 \n
\n

```
以上实例输出结果：

```
123456789
12345678
1
345
3456789
24
123456789123456789
123456789你好
------------------------------
hello
runoob
hello\nrunoob
```


# 函数
## 基本函数
### 1.输入输出函数




## 输出函数print()&输入函数input()
`print()`函数基本形式如下

```
print(value,...,sep=",end='\n')
```
其中
`value`是用户要输出的信息，可以输出多个信息（英文逗号隔开）
`sep`是输出信息之间的分隔符，默认值为一个空格
`end`是一个在`print()`函数需输出的所有信息之后添加的符号，一般为换行符

`input()`函数基本形式如下
`input([提示语])`
例子
```Python
num=input('请输入一个数字')
print(num)
```

`input()`函数获取的数据都会转化成字符串的格式



## 格式化字符串
* 占位符 （和c语言输出方法一样）
* `format()` 
    * 默认方法 
        ```python
      print('{}在 {}'.format('小明','吃饭'))
         ```
      输出结果为`小明在吃饭`
    * 设置关键字
        ```python
      print('{name}{thing}'.format(name='小明',thing='吃饭'))
        ```
       输出结果为`小明在吃饭` 
    *  设置指定位置
        ```python
        print('{1}在{0}'.format('小明'，'吃饭'))
        ```
        输出结果为`吃饭在小明
* 使用`f-string`格式化
    ```python
    name='小明'
    thing='吃饭'
    print(f'{name}在{thing}')
    ```
    输出结果为`小明在吃饭`




