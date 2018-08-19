## 1.@classmethod 修饰器

### 例如:创建一个人类

```python
class Person():
    # =========类的属性和方法==========
    # num就是类的属性，要通过类名去使用
    num = 0    #类属性的默认值

    @classmethod   #修饰器, 修饰器下面放类方法
    def show_num(cls):
    # show_num就是一个类方法：类方法就需要使用类去调用。
    # cls参数指的是当前类。调用的时候不需要给他传参,类似于self

        print('类方法：',cls.num)

    # ========对象的属性和方法=========
    # self -> 当前对象
    def __init__(self, name, age):
        # name,age都是对象的属性，就要通过对象去使用
        self.name = name
        self.age = age

    # run方法是对象方法，通过对象去调用
    def run(self):
        print('%s跑起来乌龟都追不上他' % self.name)
```

a. 通过对象使用对象属性和方法

```python
p1 = Person('hanbo',23)
print(p1.name)
p1.run()   #对象调用方法
```

b. 通过类去使用类的属性:类名.属性名

```python
Person.num = 100
print(Person.num)
```

c. 通过类去调用类的方法:类名.方法名

```python
Person.show_num()
```

## 2.@property 修饰器

定义:a.它修饰一个获取属性值的函数(修饰后他就是函数,调用属性直接对象名.函数名)
​         b.在给属性赋值的时候，需要对值进行特殊的处理或者判断的时候。不能直接给属性赋值，需要通过方法间接的赋值/或者使用属性。如果直接调用方法可能影响理解，可以通过@property修饰后可以直接使用点语法.

### 例如:创建一个人类

```python
class Person(object):
    '''人类'''
    # 注意：根据python程序员的约定，属性名前面一般都要加一个'_',告诉别人不要直接访问和修改
    def __init__(self, name, age):
        self._name = name
        self._age = age

    # getter
    # 属性getter的名字是属性名去掉_剩下的部分
    # 功能是可以通过点语法获取属性的值
    @property
    def name(self):   # 函数名取去掉属性下划线命名
        return self._name

    # setter :功能是可以通过点语法给属性赋值
    @name.setter
    def name(self, name):
        # 这里面可以进行任何操作
        self._name = name

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, age):
        if age < 0:
            age = 0
        self._age = age

p1 = Person('hanbo', 23)
print(p1.name)    #>>>hanbo
print(p1.age)     #>>>23

# 通过setter方法修改属性
p1.name = 'wangyan'
print(p1.name)   #>>>wangyan  通过setter方法赋值

p1.age = 30
print(p1.age)  #>>>30

# 注意注意:属性可以只有getter,但是不能只有setter
```

#### 练习1：定义一个Cat类，有名字，颜色，年龄对象属性，再用一个属性去统计Cat类有多少个对象。方法有吃鱼，睡觉

```python
def main():

    class Cat():

        # 类的属性
        count = 0

        def __init__(self, name):

            # 每调用一次init方法，对象个数加1
            Cat.count += 1

            self.name = name
            self.color = 'black'
            self.age = 2

        def eat_fish(self):
            print('%s在吃鱼'%self.name)

        def run(self):
            print('%s在捉老鼠'%self.name)

    cat1 = Cat('Xiao_Hua')
    print(Cat.count)    #>>>1
    cat2 = Cat('Hua_Hua')
    print(Cat.count)    #>>>2
    cat3 = Cat('Xiao_Bai')
    print(Cat.count)    #>>>3

if __name__ == '__main__':
    main()
```

#### 练习2：写一个数学类，提供加、减、乘、除的功能

```python
def main():

    class Math():

        def __init__(self):

            num = 0

        @classmethod
        def sum(cls, a, b):
            return a + b

        @classmethod
        def jan(cls, a, b):
            return a - b

        @classmethod
        def mul(cls, a, b):
            # print(num)   #不能直接在类的方法中使用对象的属性,否则报错
            return a * b

        @classmethod
        def chu(cls, a, b):
            return a / b

    reslut1 = Math.mul(10, 2)
    print(reslut1)     #>>>20
    reslut2 = Math.chu(10, 2)
    print(reslut2)     #>>>5

if __name__ == '__main__':
    main()
```





