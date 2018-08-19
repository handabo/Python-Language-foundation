# 1. input()函数的使用

**input()函数作用:**  从控制台获取用户输入的数据(输入结束标志是回车),返回的值的数据类型是字符串

```python
num = int(input("请输入学生的年龄:"))
print(num)

message = input("请输入学生的成绩:")  #返回的就是获取到的数据
print(message)
```

**windows交互式系统 (dos常用命令):**
```python
		cd   进入到指定的路径
		cd.. 返回到上级目录
		cd/  返回到根目录
		dir  查看当前文件夹下的目录和文件 (mac - ls命令)
		cls  清屏
		quit()  exit()  退出
		C/D/E/F:  直接进入到所指的盘的根目录下
```
# 2.运算符

### (1). 数学运算符: +     -    *    /    %    **   //

```python
# +:针对数字是求和.针对字符串是连接
a = 10
b = 20
c = a + b
print(c)
print(20.33 + 10)
str_1 = 'abc' + 'aaa'
print(str_1)

#针对字符串是连接
d = 'abc'
e = 123
str_2 = d + str(e)
print(str_2)

# -: 数学运算求差
print(100 - 12.0)
print('求差:' + str(100 - 12.0))

#*和/:乘和除
print('求积:' + str(2*8))
print('求商:' + str(5/2))

#%:取余
print('取余:' + str(5%2))

#** 求幂
print('2的3次方:' + str(2**3))

#//:整除
print('整除:' + str(5//2))
print('整除:' + str(4.7//2))
```

### (2). 比较运算: >   <   >=   <=   ==   !=

```python
#运算结果是布尔类型
print(3 > 2)
print(4 < 3)
print(4 <= 4)
print(5 >= 6)
print(6 == 6)
print(5 != 6)
```

### (3).赋值运算符: =   +=   -=   *=   /=   %=   **=   //=

```python
number = 10   #直接把等号右边的值,赋给左边的变量
number += 3   #number = number + 3   注意:右边的变量number必须有值
print(number)

number -= 3   #number = number - 3
print(number)

number *= 3
print(number)

number /= 3
print(number)

number %= 3
print(number)

number **= 3
print(number)

number //= 3
print(number)
```

### (4).逻辑运算符: and, or, not (与或非), 针对布尔值, 运算结果也为布尔值

```python
# and与: 两个都为True结果为True.否则为False
ret = True and True        #True
ret = True and False       #False
ret = False and False      #False
ret = 3>1 and 5>4          #True

# or或:只要有一个为True,结果就为True
ret = True or True      #True
ret = True or False     #True
ret = False or False    #False
ret = 3>2 or 1<0        #True

# not非: True为False  False为True
ret = not True     #False
ret = not False    #True
grade = 59
ret = not grade<60   #False
print(ret)
```

#### 练习1：华氏温度转摄氏温度。

```python
# F = 1.8C + 32
f = float(input('请输入华摄氏度:'))
c = (f - 32) / 1.8
print('%.1f华摄氏度等于%.1f摄氏度' % (f, c))
```

#### 练习2：输入圆的半径计算圆的周长和面积。

```python
import math
r = float(input('请输入圆的半径:'))
c = 2 * math.pi * r
s = math.pi * (r ** 2)
print('该圆的周长是:%.1f,面积是:%.1f' % (c, s))
```



