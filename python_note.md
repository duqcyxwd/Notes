# notes

1. ����ע������ָ��������
    #! /usr/bin/python 


### variable
	���԰�ȫ�ֱ����ŵ�һ��ר�ŵ��ļ��У�Ȼ��ͨ��import�����ã�
    _a = 1 
    _b = 2 

#### ��������

python��û���ṩ���峣���ı����֡������Լ�����һ����������ʵ�ֳ����Ĺ��ܡ�

    class _const:  
    class ConstError(TypeError): pass 
    def __setattr__(self,name,vlaue):  
    if self.__dict__.has_key(name):  
    raise self.ConstError, ��Can��t rebind const(%s)��%name  
    self.__dict__[name]=value  
    import sys  
    sys.modules[__name__]=_const() 


####���������͡�

1. python���������ͷ�Ϊ���͡������͡������͡������͡��������͡�
2. �����Ҫ�鿴���������ͣ�����ʹ��type�࣬������Է��ر��������ͻ򴴽�һ���µ����͡�
3. python��3�ֱ�ʾ�ַ������͵ķ�ʽ���������š�˫���š������š������ź�˫���ŵ���������ͬ�ġ�python����Ա��ϲ���õ����ţ�C/Java����Ա��ϰ��ʹ��˫���ű�ʾ�ַ������������п������뵥���š�˫���Ż��е��ַ���

### ��������ͱ��ʽ��
1. i+=1�ǿ��Ե�
2. ������Ϊ!=��<>
3. �߼����ʽ��and��ʾ�߼��룬or��ʾ�߼���not��ʾ�߼���

### ��������䡿
1. if
	if (���ʽ) :
    	���1
    else :
    	���2 
2. for(i=0;i<5;i++)
	for x in range(0,5,2):
    	print x 

### ��������ء�
1. Ԫ�飨tuple����python��һ�����õ����ݽṹ��Ԫ���ɲ�ͬ��Ԫ����ɣ�ÿ��Ԫ�ؿ��Դ洢��ͬ���͵����ݣ����ַ�������������Ԫ�ء�Ԫ����д�����ģ���Ԫ�鴴��֮�������޸ġ�Ԫ����������һ�����ݣ���Ԫ���е�Ԫ�ش���ͬ����������԰�Ԫ�鿴�������޸ĵ����顣����Ԫ��ʾ�����£�

    tuple_name=(��apple��,��banana��,��grape��,��orange��) 

2. �б�list�����б��Ԫ�����ƣ�Ҳ��һ��Ԫ����ɣ��б����ʵ����ӡ�ɾ���Ͳ��Ҳ�����Ԫ�ص�ֵ���Ա��޸ġ��б��Ǵ�ͳ�����ϵ����顣�б���ʾ�����£�

    list=[��apple��,��banana��,��grage��,��orange��] 

	����ʹ��append��������β��׷��Ԫ�أ�ʹ��remove��ɾ��Ԫ�ء�

3. �ֵ䣨dictionary�����ɼ�-ֵ����ɵļ��ϣ��ֵ��е�ֵͨ���������á�����ֵ֮����ð�Ÿ�������-ֵ��֮���ö��Ÿ��������ұ�������һ�Ի������С�����ʾ�����£�

    dict={��a��:��apple��, ��b��:��banana��, ��g��:��grage��, ��o��:��orange��} 

4. ���У������Ǿ�����������Ƭ�����ļ��ϡ�Ԫ�顢�б���ַ������������С�

### I/O
1. �򵥴����ļ���

    context=��hello,world��
    f=file(��hello.txt��,��w��)
    f.write(context);
    f.close() 

2. ��ȡ�ļ�����ʹ��readline()������readlines()������read������

3. д���ļ�����ʹ��write()��writelines()����


### Object && Class
1.
	class Fruit:
		def grow(self):
			print ��Fruit grow�� 
2. pythonʹ�ú�����staticmethod()����@ staticmethod��ָ��ķ�������ͨ�ĺ���ת��Ϊ��̬��������̬�����൱��ȫ�ֺ�����
3. �̳е�ʹ�÷�����
	class Apple(Fruit):


### connect SQL
Example:

	import os, sys
	import MySQLdb
	try:
	    conn MySQLdb.connect(host=��localhost��,user=��root��,passwd=����,db=��address��
	except Exception,e:
	    print e
	    sys.exit()
	cursor=conn.cursor()
	sql=��insert into address(name, address) values(%s, %s)��
	value=((��zhangsan��,��haidian��),(��lisi��,��haidian��))
	try
	    cursor.executemany(sql,values)
	except Exception, e:
	    print e
	sql=��select * from address��
	cursor.execute(sql)
	data=cursor.fetchall()
	if data
	    for x in data:
	        print x[0],x[1]
	cursor.close()
	conn.close()


## �ɼ���
    �ڽ��ж�����ʱ�����һ�����Ե��������������»��߿�ʼ��ͬʱ�ֲ������»��߽����ģ���ô���ڱ���ʱ���Զ��ر���дΪ��������������

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
