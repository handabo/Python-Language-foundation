# pygame常规操作

### 导入模块

import pygame              # 导入pygame模块

from sys import exit     # 导入退出鼠标点击事件

from math import pi     # 导入math模块π

import time                    # 导入时间模块

### 1.初始化pygame

```python
pygame.init()
```

### 2.创建窗口大小

```python
# 第一个参数: 设置窗口的大小
# 第二个参数: 设置窗口的样式（默认值是0），RESIZABLE->窗口可通过鼠标让其大小发生改变
# 第三个参数: 不建议设置
screen = pygame.display.set_mode((500, 300), pygame.RESIZABLE, 0)
```

### 3.设置窗口的填充背景颜色

```python
# 颜色值 -> RGB
# RGB:三原色红(R)、绿(G)、蓝(B)
# (1).根据R,G,B的值的不同，可以创建出不同颜色
# (2).R,G,B的取值范围是0-255  白色:(255,255,255) 黑色：（0，0，0）
# (3).RGBA:RGB+透明度
screen.fill((255, 255, 255))
```

### 4.设置窗口的标题

```python
pygame.display.set_caption('hello，pygame')
```

### 5.获取屏幕的宽度

```python
w = screen.get_width()
print(w)
```

### 6.获取屏幕的高度

```python
h = screen.get_height()
print(h)
```

### 7.画直线

```python
# aaline(Surface, color, startpos, endpos, blend=1)
# startpos:起始点的位置
# endpos：结束位置
pygame.draw.aaline(screen, (10, 200, 120), (20, 20), (200, 200))
```

### 8.画矩形点

```python
# aalines(Surface, color, closed, pointlist, blend=1)
# closed: 是否关闭(是否连接起始点和终点)
# pointlist:需要画线连接的点的列表
pygame.draw.aalines(screen, (100,50,20), True,[(10,10),(60,20),(30,100),(100,120)])
```

### 9.画矩形

```python
pygame.draw.rect(screen,(28,164,252),(340,360,120,200), 0)
```

### 10.画弧线

```python
# arc(Surface, color, Rect, start_angle, stop_angle, width=1)
# Rect:((x,y),(width, height))
# start_angle:其实角度，角度是pi对应的角度值
pygame.draw.arc(screen, (100,100,100),((250,150),(100,100)),pi/2,pi)
```

### 11.画圆

```python
# circle(Surface, color, pos, radius, width=0):
# 参数1(Surface)：告诉pygame圆画在什么地方
# 参数2(color):颜色
# 参数3(pos):位置（x,y）,注意不要超过屏幕的范围，指的是圆心的位置
# 参数4(radius):半径
# 参数5(width):宽度，值为0的是就填充
pygame.draw.circle(screen, (0, 255, 0), (50, 50), 40, 10)
```

### 12.使用系统的字体

```python
# a.在窗口上显示文字
# SysFont(name, size, bold=False, italic=False, constructor=None)
# name:字体名
# size:字体大小
# bold：是否加粗 
# italic：是否斜体
font = pygame.font.SysFont('arial', 20, True, True)

# b.将文字渲染到屏幕
# render(self, text, antialias, color, background=None)
# text:文字
# antialias:是否平滑渲染
# color：文字颜色
screen.blit(font.render('hello,world', True, (255, 0, 0)), (100, 100))
```

### 13.使用自定义字体

```python
font1 = pygame.font.Font('./font/maobi.ttf', 30)
screen.blit(font1.render('你好世界', True, (0 ,0 ,255)), (20, 20))
```

### 14.渲染图片

```python
# (1)加载图片
image = pygame.image.load('./images/hanbo.png').convert_alpha()

# (2)操作图片
# a.获取图片的大小
print(image.get_size())

# b.改变图片大小
scale(Surface, (width, height), DestSurface=None)

# c.将指定图片，缩放成指定的大小
new_image = pygame.transform.scale(image, (50, 50))

# d.将指定的图片旋转并且缩放
# rotozoom(Surface, angle, scale)
# Surface：被操作的图片对象
# angle：旋转角度(度数(0-360))
# scale:缩放比例(缩小->小于1，放大->大于1)
new_image1 = pygame.transform.rotozoom(image, 90, 0.5)

# e.渲染图片到屏幕
screen.blit(new_image1, (0, 0))     #括号里面是x, y坐标
screen.blit(new_image2,(300, 100))
```

### 15.加载音乐文件

```python
Path = r'G:\KuGou\music\qw.mp3'  #打开文件路径
pygame.mixer.init()           #对pygame进行初始化操作
pygame.mixer.music.load(Path)   # 加载音乐
pygame.mixer.music.play()   # 播放音乐
time.sleep(360)            #播放时间长度
pygame.mixer.music.stop()   #停止播放

# pygame.init() 进行全部模块的初始化，
# pygame.mixer.init() 或者只初始化音频部分
# pygame.mixer.music.load('xx.mp3') 使用文件名作为参数载入音乐,载入的音乐不会全部放到内容中，
# 而是以流的形式播放的，即在播放的时候才会一点点从文件中读取。
# pygame.mixer.music.play()播放载入的音乐。
# pygame.mixer.music.play(loops=0, start=0.0) loops和start分别代表重复的次数和开始播放的位置。
# pygame.mixer.music.stop() 停止播放，
# pygame.mixer.music.pause() 暂停播放。
# pygame.mixer.music.unpause() 取消暂停。
# pygame.mixer.music.fadeout(time) 用来进行淡出,在time毫秒的时间内音量由初始值渐变为0,最后停止播放。
# pygame.mixer.music.set_volume(value) 来设置播放的音量，音量value的范围为0.0到1.0。
# pygame.mixer.music.get_busy() 判断是否在播放音乐,返回1为正在播放。
# pygame.mixer.music.set_endevent(pygame.USEREVENT + 1) 在音乐播放完成时，用事件的方式通知用户程序.
```

### 16.将内容渲染到窗口上(让最近绘制的屏幕可见)

```python
pygame.display.flip()
```

### 17.事件窗口循环

```python
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            # 系统的退出函数
            exit()
```

### 18.鼠标和按键的点击事件

```python
runing = True
while runing:

    # 不断的去检测是否有事件发生，通过event就可以获取到当前发生的事件
    for event in pygame.event.get():

        # 如果用户点了窗口最上面的关闭按钮后会产生QUIT事件
        if event.type == pygame.QUIT:
            # runing = False   或者 runing = False结束循环,退出窗口
            # 系统的退出
            exit()

        # 鼠标按下,pos是鼠标所在的位置，pygame中的位置都是由x坐标和y坐标确定的
        if event.type == pygame.MOUSEBUTTONDOWN:
            print('鼠标按下')
            pos = event.pos
            print(pos)

        # 鼠标移动
        if event.type == pygame.MOUSEMOTION:
            print('鼠标移动')
            pos = event.pos
            print(pos)

        # 按键按下
        if event.type == pygame.KEYDOWN:
            print('按键按下')
            key = event.key
            print(chr(key))

        # 按键弹起
        if event.type == pygame.KEYUP:
            print('键盘的按键被按下弹起')
            key = event.key
            print(chr(key))

        if event.type == pygame.VIDEORESIZE:
            print('窗口大小改变:',event.size)

# Unicode = ASCII码 + 万国码
# 扩充:chr():将ASCII码转换成字符     ord():将字符转换成ASCII码.
```

### 19.延迟时间

```python
pygame.time.delay(50)
```

### 20.创建pygame的基本结构如下:

```python
import pygame
from sys import exit


def main():
    pygame.init()  # 初始化游戏并创建一个屏幕对象
    screen = pygame.display.set_mode((1000, 600))
    pygame.display.set_caption('hello，pygame')
    screen.fill((255, 255, 255))

    # 在这中间添加游戏过程

    pygame.display.flip()  # 让最近绘制的屏幕可见
    while True:  # 开始游戏的主循环
        for event in pygame.event.get():  # 监视键盘和鼠标事件
            if event.type == pygame.QUIT:
                exit()


if __name__ == '__main__':
    main()
```

### 21.练习,画一个台球运动的效果

```python
import  pygame
from  sys import exit

def main():
    pygame.init()

    screen = pygame.display.set_mode((400,300))
    screen.fill((255, 255, 255))

    image = pygame.image.load('images/hanbo.png').convert_alpha()
    image = pygame.transform.scale(image, (80, 80))
    screen.blit(image, (0, 0))

    pygame.display.flip()
    x = 0
    y = 0
    xspeed = 10
    yspeed = 10

    while True:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                exit()

             # 以下6行代码是图片跟着鼠标一起移动
	#		if event.type == pygame.MOUSEMOTION:
	#			"""拿到鼠标的位置"""
	#			x,y = event.pos
	#			screen.fill((255, 255, 255))
	#			screen.blit(image, (x - 40, y - 40))
	#			pygame.display.flip()


        """延迟50毫秒"""
        pygame.time.delay(50)

        """自动移动"""
        x += xspeed
        y += yspeed
        screen.fill((255, 255, 255))
        screen.blit(image,(x, y))
        pygame.display.flip()

        if x<0 or x+80>400:
            xspeed = -xspeed

        if y<0 or y+80>300:
            yspeed = -yspeed

if __name__ == '__main__':
    main()
```



```python

from enum import Enum,unique

import pygame

# 经验:枚举是定义符号常量的最佳选择
#      符号常量优于字面常量
@unique
class Direction(Enum):
    UP = 0
    RIGHT = 1
    DOWN = 2
    LEFT = 3
    
    
# 红绿蓝取值都在255之间
```





