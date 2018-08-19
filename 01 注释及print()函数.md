 # 注释及print()函数

### 1.注释:

**注释的作用**: a.对代码进行说明备注; b.关闭程序中的某些功能.    在代码中不会被编译执行的部分(不会起到任何程序作用,用来备注 说明用的.)

**单行注释**:  #

**多行注释**:  ''' '''      """  """

**快捷键**:  Ctrl+/

**建议**:  写程序一定要多写注释.

**python特点**:   每条语句结束后可以不写分号.如果一行要写多条语句,那么每条语句之间必须使用分号隔开.

### 2.print()函数:

是一个系统提供的函数, 作用是在控制台打印括号里面的内容.

"hello world"是一个字符串,字符串的内容就是双引号里面的内容.

```python
print('hello world!')
print('hello python!')
print('hello world!'); print('hello python!')
```

### print()总结:

#### (1).直接打印数值

```python
print("asss")
print(123)
print(True)
```

#### (2).直接打印变量
```python
name = 'hanbo'
print(name)
```

#### (3).可以同时打印多个变量,每个变量要用逗号隔开
```python
age = 24
print(name,123,age,age+10)
```



#### (4).支持格式化输出
​	%s  给字符串占位

​	%d  给整数占位

​	%f  给浮点数占位(%.数字f:数字的值是多少，输出就会保留几位小数，小数截取的时候会做四舍五入操作。)

**总结**:  格式输出符的个数和类型要和输出的值列表一一对应(包括类型和数量)

```python
weight = 62.372571
print("体重:%.1f" % weight)
```

参数end=' '     用来设置打印结束的结束符，默认是"\n"
参数sep=' '     用来分割print中同时打印的多个值，默认是" "

```python
print("第一次打印",end=" ")
print("第二次打印")
print("第三次打印")
print(123,"aaa",sep = "--")
```

```python
dog_name = input('请输入狗的名字:')
dog_age = int(input('请输入狗的年龄:'))
dog_color = input('请输入狗的颜色:')
print('我家的狗狗',dog_name,',今年',dog_age,'岁,它的颜色是',dog_color,'!',sep='')
```

```python
age = 26
print('你的年龄是:'+ str(age))
print('你的年龄是%d' % age)
name = '韩波'
print('%s的年龄是%d' % (name,age))
```

### 练习:  打印我家狗的姓名,年龄,颜色
```python
dog_name = '泰迪'
dog_age = 5
dog_color = '棕色'
print('我家的狗狗%s今年%d岁,它的颜色是%s' % (dog_name, dog_age, dog_color))

dog_name = input('请输入狗的名字:')
dog_age = int(input('请输入狗的年龄:'))
dog_color = input('请输入狗的颜色:')
print('我家的狗狗%s今年%d岁,它的颜色是%s' % (dog_name, dog_age, dog_color))
```



