## 1.slots魔法方法(绑定对象属性)

python是动态语言,我们可以给对象添加属性和删除属性.

slots作用: 就是限制类的属性(绑定属性), 除了被绑定的属性名以外不能给对象添加其他属性.

注意: 给对象添加属性,只能添加slots绑定的属性名.不能限制类属性的

### 例如:创建一个人类

```python
class Person(object):

	__slots__ = ('name', 'age')   # 添加属性需要在slots里面添加
	def __init__(self, name, age):
		self.name = name
		self.age = age

p1 = Person('handabo', 20)
# p1.names = 'wangyan'   # 如果出现这种情况  不想自己添加属性  这时需要slots方法
# print(p1.names)
del p1.name  #slots不影响对象属性的删除
```

## 2.静态方法

静态方法也是类方法,要通过类去调用.和类方法的区别就是没有默认参数cls.
关键字:@staticmethod

### 例如:创建一个班级类

```python
class Class(object):
	'''班级类'''

	# 类方法
	@classmethod
	def foo(cls):
		print('大家好,我是1班') 

	# 静态方法
	@staticmethod
	def foo_1():
		print('大家好,我是2班')

Class.foo()    #>>>大家好,我是1班
Class.foo_1()  #>>>大家好,我是2班
```

## 3.运算符的重载方法

在类中可以通过实现 __gt__ 和 __lt__ 以及 __add__ 和 __sub__等方法来对>, <, +, -运算符进行重载

### 例如:创建一个学生类

```python
class Student(object):
    """学生类"""

    def __init__(self, name, age, score):
        self.name = name
        self.age = age
        self.score = score

    # 重载>  告诉比较两个Student对象的时候，怎么比
    def __gt__(self, other):
        return self.age > other.age

    # 重载<
    def __lt__(self, other):
        return self.score < other.score

    # 重载+
    def __add__(self, other):
        return self.score + other.score

    # 重载-
    def __sub__(self, other):
        return self.age - other.age

stu1 = Student('LiuDeHua', 40, 88)
stu2 = Student('ZhangXueYou', 35, 90)

#可以通过==判断两个对象是否相等（比较的是stu1和stu2存的地址是否相等）
print(stu1 == stu2)   #>>>False

# 打印重载结果
print(stu1 > stu2)   #>>>True
print(stu1 < stu2)   #>>>True
print(stu1 + stu2)   #>>>178
print(stu1 - stu2)   #>>>5
```

