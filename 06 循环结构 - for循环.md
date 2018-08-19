# 循环分支结构

**循环结构:** 在开发中遇到需要重复的做某见事情的时候,需要用到循环结构.

python中提供的循环结构有**两种**: for循环,   while循环.

**for循环**:一般在知道循环次数的时候使用.

**while循环**:一般在不知道循环次数的时候使用.

### 1.for 循环

```python
for循环的结构
for 变量 in 范围:
	循环体(循环执行语句)
    
for的功能:让变量依次去取指定范围中的值,
          直到范围中的值取完为止.每取到一个值执行一次循环体
```

```python
# range(0, 6): 左闭右开,依次加1
# range(0, 6, 2):左闭右开.依次加2,第三个元素是步长.
# range(10):0,1,2,3,4,5,6,7,8,9,10
for i in range(0, 6, 2):
	print(i)
    
#扩充知识点:
import random
# 随机产生一个1-100的整数
num = random.randint(1,100)
print(num)

# 随机产生一个1-100的浮点数
num = random.uniform(1,100)
print(num)

# 随机产生一个步长为2的整数
num = random.randrange(0,101,2)
print(num)
```

### 2.for循环嵌套

```python
例如:
for i in range(1, 10):
	for j in range(1, i+1):
		print()
```

### 3.continue 和 break 的使用

**(1).continue:**  提前结束本次循环(不再执行continue后的循环语句)

```python
# 打印1-10,但是不打印5
for i in range(1, 11):
	if i == 5:
		continue
	print(i, end = ' ')
    
#练习: 计算1-100中所有能被5整除的数的和,要求用continue.
num = 0
for x in range(1, 101):
	if x % 5 != 0:
		continue
	num += x
print(num)
```

**(2). break:** 结束整个循环.

```python
# 打印1-10,但是当打印到5时结束整个循环.
for a in range(1, 11):
	if a == 5:
		break
	print(a, end = ' ')

# 练习: 找出101-200之间第一个能被7整除的数,并打印.
for b in range(101, 201):
	if b % 7 == 0:
		print(b)
		break
```

#### 练习1: 求1+2+3+...+100的和.

```python
Version:0.0.1
Author:韩波
Date:2018.5.10
  
sum1 = 0
for x in range(1, 100+1):
	# sum1 = sum + 1
	sum1 += x
	print(x, sum1)
# print(sum1)
```

#### 练习2:  求1*2*3*...*100的积.

```python
num2 = 1
for i in range(1,20+1):
	# num2 = num2 * i
	num2 *= i
	print(num2, end = ',')
```

#### 练习3: 找出1到100中所有可以被3整除的数.

```python
for y in range(1, 100+1):
	if y % 3 == 0:
		print(y, end = ' ')
```

#### 练习4: 给出一个不多于5位的正整数, 要求:1.求它是几位数?

```python
num3 = int(input('请输入一个不超过5位数的正整数:'))
count = 1
temp = num3
for x in range(1, 6):
	temp //= 10
	if temp != 0:
		count += 1
print('%d是%d位数' % (num3, count))
```

#### 练习5: 求10的阶乘.

```python
num4 = 1
for i in range(1, 11):
	num4 *= i
print(num4)
```

#### 练习6: 求阶乘之和: 1! + 2! + 3! + ... n!

```python
num5 = 0
for x in range(1, 4):
	num6 = 1
	for y in range(1, x+1):  # 循环结束后num6存的是X.
		num6 *= y
	num5 += num6    # 把每次求的得的阶乘累加起来
print(num5)
```

#### 练习7: 九九乘法表.

```python
for x in range(1, 10):
    for y in range(1, x+1):
        print('%d * %d = %d' % (y, x, x*y), end='\t')
    print()
```

#### 练习8: 打印出所有的水仙花数,所谓水仙花数是指一个三位数，其各位数字立方和等于该			数本身。如水仙花数153:  153 = 1^3 + 5^3 + 3^3

```python
for i in range(100, 1000):
    a = i // 100        #百位
    b = i // 10 % 10    #十位
    c = i % 10          #个位
    if i == a**3 + b**3 + c**3:
        print('%d是水仙花数' % i)
```

#### 练习9:  有一对兔子，从出生后第3个月起，每个月都生一对兔子，小兔子长到第三个月后每个月又生一对兔子，假如兔子都不死，问每个月的兔子总数为多少？

```python
month = int(input('请输入你想查看的第几个月:'))
num = 1  # 初始兔子的数量
n1 = 1   #第一月的兔子数量
n2 = 1   #第二月的兔子数量
for n in range(1, month + 1):
    if n == 1 or n == 2:
        num = 1          # 一\二月的老兔子
    else:
        num = n1 + n2   #第三月.....n个月的的兔子数量
        n1 = n2
        n2 = num
print('第%d个月的兔子总数有%d只' % (month, num))
```

#### 练习10:  有一分数序列：2/1,  3/2,  5/3,  8/5,  13/8,  21/13...求出这个数列的第20个分数

```python
for x in range(1, 21):
    if x == 1:
        num1 = 2     #分子
        num2 = 1     #分母
    else:
        temp = num1
        num1 = num1 + num2
        num2 = temp
print('第20个分数是:%d/%d' % (num1, num2))
```

#### 练习11: for循环嵌套打印正方形

```python
print('打印实心正方形-----------------------------------------')
for a in range(1, 9):      # 双for循环
    for b in range(1, 9):
        print('*', end='  ')
    print()

print('单for循环')          #单for循环
for a1 in range(1, 9):
    print('  *' * 8, end='')
    print()

print('打印空心正方形-----------------------------------------')
for i in range(1, 9):            # 双for循环
    if (i == 1) | (i == 8):
        for j in range(1, 9):
            print('*', end='  ')
    else:
        for j in range(1):
            print('*', end='  ')
        for j in range(6):
            print(' ', end='  ')
        for j in range(1):
            print('*', end='  ')
    print()

for i1 in range(1, 9):             #单for循环
    if (i1 == 1) | (i1 == 8):
        print('  *' * 8, end='')
    else:
        print('  *' + '   ' * 6 + '  *', end='')
    print()
```

#### 练习12: for循环嵌套打印三角形

```python
print('打印实心三角形---------------------------------------------')
for c in range(1, 6 + 1):
    for d in range(1, 7 - c):
        print(' ', end='  ')
    for e in range(0, 1 + 2 * (c - 1)):
        print('*', end='  ')
    print()

print('打印直角三角形---------------------------------------------')
for g in range(1, 11):
    for h in range(1, g + 1):
        print('*', end='  ')
    print()

print('打印等腰三角形---------------------------------------------')
for i in range(1, 11):
    for j in range(1, 11 - i):
        print(' ', end='')
    for h in range(1, i + 1):
        print('*', end=' ')
    print()

print('单for循环打印三角形----------------------------------------')
for q in range(0, 11):
    print('  *' * (q + 1), end='')
    print()
```



