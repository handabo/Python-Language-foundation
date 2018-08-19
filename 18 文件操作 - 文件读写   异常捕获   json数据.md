# 文件读写   异常捕获   json数据

### 1.文件读写

**文件:** 可以让数据持久化（.db,.sqlite,）

**文件的读写操作对象:** （文本、二进制文件(图片、音频、视频)、json(重点)）

**文件读写操作步骤:**   a.打开文件    b.读、写文件

#### (1)对文本文件进行读写操作

**a.  读文件的步骤:**打开文件(以读的形式打开) ---> 读取文件内容 --->关闭文件

**b.  open**(文件名/文件地址，打开方式，编码格式):返回值是被打开的文件对象

**c.  打开文件的方式:**
 r(读)
 rb(读二进制,以二进制格式读取)

 w(写)
 wb(写二进制,以二进制格式写入)
 a(写,打开用于追加的文件,如果被写入的该文件不存在，它会创建一个用于写入的新文件)

**注意:**  a.当文件和当前模块在同一个文件夹里的时候可以直接写文件名。否则就使用文件地址

​	  b.文本编码格式:一般都用 utf-8

**相关函数:**

**read()：**获取文件所有的内容，返回值是字符串

**close():**  关闭文件

**readlines():**  获取文件所有的内容，返回的是以每一行的内容为元素组成的列表

**readline():**  读取当前行的多少个文字

#### 例如:   打开 程序人生.txt文件

```python
#1.如果文件在当前路径,直接传文件名
p = open('程序人生.txt','r',encoding='utf-8')

#2.如果文件没在当前路径,则需要输入路径
p = open('G:\py\程序人生.txt','r',encoding='utf-8')

read():返回读到的内容  
print(p.read())

close():关闭文件(一定是在对文件操作完了再关)
p.close()

#3. 以with open() as x:这种方式打开文件，文件会自动关闭
with open('程序人生.txt','r',encoding='utf-8') as f1:
    text_list = f1.readlines()    #获取文件所有的内容，返回的是以每一行的内容为元素组成的列表
    for line in text_list:
        print(line)

with open("程序人生.txt",'r',encoding='utf-8') as f2:
    print(f2.readline(5))  #调用一次读一行

    # 遍历取出来的数据
    for x in f2:   #每次循环x会取出文件中的一行内容
        print(x)
```

#### (2).对文本文件进行写操作

**步骤:**  打开文件 ---> 写 
**w** ---> 通过调用写的方法，写入的内容会覆盖原来的内容
**a** ---> 通过调用写的方法，写入的内容会添加到文件后面

**write():** 写入内容 
**writelines():** 写入一行内容

```python
#例如:
with open('程序人生.txt','a',encoding='utf-8') as fw:
fw.write("\naaaaaaaaaaaaa")
fw.writelines(['\n1111111','\n2222222','\n3333333'])

# 注意:如果是以写的方式打开文件，如果文件不存在，会自动创建该文件
# 例如:
with open('111.txt','a',encoding='utf-8') as f2:
    f2.write('坚持到无能为力,拼搏到感动自己')    #这里会创建一个新的111.txt文件
```

### 2.二进制文件的读写

```python
# a.读取
with open('G:\py\风景.png','rb') as fb:  #读取图片
    data = fb.read()
    print(data)  #>>>b'\xff\xd8\xff\xe0\x00\x10JFIF...
    
# b.写入
with open('汽车.png','wb') as fb:
    fb.write(data)    #写入风景.png的二进制到汽车.png,创建一个新的图片文件
```
### 3.异常捕获

**异常捕获:** 如果希望在程序发生错误的时候，程序还可以继续执行，这个时候就需要去捕获异常.
**try:** 把会出现异常的代码放在try:里面

```python
# 例如:
try:
    # 可能会出现异常的代码
    with open('程序人生.txt','r',encoding='utf-8') as ff:
        ff.read()
except LookupError:  #获取异常类型（）
    # 异常发生的时候不会崩溃，而是执行这个里面的代码
    print("异常发生了")
except FileNotFoundError:
    print("文件找不到")
finally:   #不管异常是否发生都会执行
    print("结尾")
    
print('----------------------------------------------------------)
      
try:
    num = int("uuu23")
except:
    print("只有纯数字字符串才能转换成整型")
print(num)  #报错
```
### 4.json数据

**json数据:** 是目前数据传输使用的最广发的一个数据格式

**模块:** import json

```python
#json数据格式对应python的集几种形式:
{} Dict ---> 字典
[] list ---> 列表
"" ---> 字符串
1  ---> 整型数据
小数 ---> 浮点型
null ---> None
rue/false ---> True/False
```

#### (1)读取json文件

**A.注意注意:**a.所有的文件操作都是在文件打开的前提下进行的!!!

​		b.json中只能存储一个大的列表或者一个大的字典

​		c.打开json文件进行写操作的时候只能使用'w'方式去打开

**B.dump()和load()**

**json.dump():**将 Python 对象编码成 JSON 字符串

**json.load():**将已编码的 JSON 字符串解码为 Python 对象

**C.将数据写入json文件中步骤:**  第一个参数:传字典、列表          第二个参数:传文件对象
```python
#例如:
with open('ikang.json','w',encoding='utf-8') as js:
    person = {'name':'hanbo','age':22,'grade':[100,99,88]}
    json.dump(person,js)
    classes = [person,person,person]
    json.dump(classes,js)
```

#### (2)获取json文件的内容

```python
with open('ikang.json','r',encoding='utf-8') as fs:
    result = json.load(fs)  #返回值要么是列表要么就是字典
    print(result)
    result.append(100)
    print(result)

with open('luffy.json','w') as fs:
    json.dump(result,fs)
```

#### 练习：用一个列表存储多个学生信息（名字，年龄，电话），要求数据持久化。删除某个学生的信息，再更新文件

```python
stu1 = {'name':'张珊','age':20,'tel':'133'}
stu2 = {'name':'李思','age':22,'tel':'177'}
stu3 = {'name':'王麻仔','age':32,'tel':'189'}
studens = [stu1,stu2,stu3]
studen_file_name = "student.json"
with open(studen_file_name,'w',encoding='utf-8') as fs:
    json.dump(studens,fs)

with open(studen_file_name,'r') as fs:
    studens = json.load(fs)
    print(studens)
    for stu in studens:
        if stu['name'] == '李四':
            studens.remove(stu)
            break
    print(studens)

with open(studen_file_name,'w') as fs:
    json.dump(studens,fs)
```



