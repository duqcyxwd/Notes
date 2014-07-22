# notes

1. 如下注释用于指定解释器
    #! /usr/bin/python 


### variable
	可以把全局变量放到一个专门的文件中，然后通过import来引用：
    _a = 1 
    _b = 2 

#### 【常量】

python中没有提供定义常量的保留字。可以自己定义一个常量类来实现常量的功能。

    class _const:  
    class ConstError(TypeError): pass 
    def __setattr__(self,name,vlaue):  
    if self.__dict__.has_key(name):  
    raise self.ConstError, “Can’t rebind const(%s)”%name  
    self.__dict__[name]=value  
    import sys  
    sys.modules[__name__]=_const() 


####【数据类型】

1. python的数字类型分为整型、长整型、浮点型、布尔型、复数类型。
2. 如果需要查看变量的类型，可以使用type类，该类可以返回变量的类型或创建一个新的类型。
3. python有3种表示字符串类型的方式，即单引号、双引号、三引号。单引号和双引号的作用是相同的。python程序员更喜欢用单引号，C/Java程序员则习惯使用双引号表示字符串。三引号中可以输入单引号、双引号或换行等字符。

### 【运算符和表达式】
1. i+=1是可以的
2. 不等于为!=或<>
3. 逻辑表达式中and表示逻辑与，or表示逻辑或，not表示逻辑非

### 【控制语句】
1. if
	if (表达式) :
    	语句1
    else :
    	语句2 
2. for(i=0;i<5;i++)
	for x in range(0,5,2):
    	print x 

### 【数组相关】
1. 元组（tuple）：python中一种内置的数据结构。元组由不同的元素组成，每个元素可以存储不同类型的数据，如字符串、数字甚至元素。元组是写保护的，即元组创建之后不能再修改。元组往往代表一行数据，而元组中的元素代表不同的数据项。可以把元组看做不可修改的数组。创建元组示例如下：

    tuple_name=(“apple”,”banana”,”grape”,”orange”) 

2. 列表（list）：列表和元组相似，也由一组元素组成，列表可以实现添加、删除和查找操作，元素的值可以被修改。列表是传统意义上的数组。列表创建示例如下：

    list=[“apple”,”banana”,”grage”,”orange”] 

	可以使用append方法来在尾部追加元素，使用remove来删除元素。

3. 字典（dictionary）：由键-值对组成的集合，字典中的值通过键来引用。键和值之间用冒号隔开，键-值对之间用逗号隔开，并且被包含在一对花括号中。创建示例如下：

    dict={“a”:”apple”, “b”:”banana”, “g”:”grage”, “o”:”orange”} 

4. 序列：序列是具有索引和切片能力的集合。元组、列表和字符串都属于序列。

### I/O
1. 简单处理文件：

    context=”hello,world”
    f=file(“hello.txt”,’w’)
    f.write(context);
    f.close() 

2. 读取文件可以使用readline()函数、readlines()函数和read函数。

3. 写入文件可以使用write()、writelines()函数


### Object && Class
1.
	class Fruit:
		def grow(self):
			print “Fruit grow” 
2. python使用函数”staticmethod()“或”@ staticmethod“指令的方法把普通的函数转换为静态方法。静态方法相当于全局函数。
3. 继承的使用方法：
	class Apple(Fruit):


### connect SQL
Example:

	import os, sys
	import MySQLdb
	try:
	    conn MySQLdb.connect(host=’localhost’,user=’root’,passwd=’’,db=’address’
	except Exception,e:
	    print e
	    sys.exit()
	cursor=conn.cursor()
	sql=’insert into address(name, address) values(%s, %s)’
	value=((“zhangsan”,”haidian”),(“lisi”,”haidian”))
	try
	    cursor.executemany(sql,values)
	except Exception, e:
	    print e
	sql=”select * from address”
	cursor.execute(sql)
	data=cursor.fetchall()
	if data
	    for x in data:
	        print x[0],x[1]
	cursor.close()
	conn.close()


## 可见性
    在进行定义类时，如果一个属性的名称是以两个下划线开始，同时又不是以下划线结束的，那么它在编译时将自动地被改写为类名加上属性名

    class Greeting:
        __data = "Hello World!"
        def __init__(self, str):
            Greeting.__data = str
    >>> g = Greeting("Hello Gary!")
    >>> dir (g)
    ['_Greeting__data', '__doc__', '__init__', '__module__']



## Cygwin
alias python='/cygdrive/c/My\ Program/Python/python.exe -i


## Question
	Qt, emit

# sublime debug
sublime.status_message("sadf")
sys.stderr.write("started\n")
