# Python 第一天

## 1、基础起步

### 1、Python

​	Python是荷兰人*Guido* van Rossum圣诞节无聊开发的，现在我们使用Python3.x版本

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/龟叔照片.jpg)

​	在计算机中有诸多的编程语言，Python是其中的一种，简洁而优雅，易上手

​	编程语言？就像我们交流需要说中文，我和老外交流需要用英文，那么和计算机交流就要说计算机认识的

​	当然了，计算机并不是那么智能，它并不认识我们写的代码

```python
a = 1
```

​	比如上面这一句，把1给变量a，那么计算机会把它翻译成：

```
1011 1000 0000 0001 0000 0000 0000 0000 1001 0000 1001 0000
```

​	这么一堆二进制，那么查错不好查，修改不好改，所以才出现了我们的高级编程语言，Python、C/C++等等都是高级语言，汇编语言和机器语言都是低级语言，**我们只需要知道，不管我们写了什么，存了什么，以什么方式，到计算机中都是二进制，也就是那一堆0和1**



### 2、应用领域

- 人工智能
- 网络爬虫
- web开发
- 信息安全
- 等等

​	它应用领域特别广，像爬虫等薪资很高，本课程针对零基础学员，多练习即可



## 2、Python部署

​	首先我们需要安装Python的解释器，因为我们上面说了，计算机只认识二进制

​	我们需要解释器来将代码转换为计算机认识的语言，Python是一门解释型的语言，也就是一边执行一边翻译

​	[Welcome to Python.org](https://www.python.org/)

​	首先我们打开上面的这个Python官网

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/download.jpg)

​	直接点击这个Python 3.xx.x，会自动根据系统选择一个合适的版本下载，然后打开下载的安装文件，就可以开始我们的安装步骤了

​	因为我这里安装过了，所以我只标注安装方法就好了

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/start.jpg)

​	点击上面这个customize，下面的Add to PATH一定要勾选，否则没法用

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/option.png)

​	默认全勾选，继续Next就行了

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/modify.jpg)

​	为所有用户安装，可以选择，路径修改也可以修改，直接点击安装

​	按下键盘的Win+R键，然后输入cmd，输入python进入cmd的交互界面

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/cmd.png)

​	此时输入一条命令：print('Hello World')，我们的第一个编程之旅就开始了，注意标点符号要全英文的，如果出现中文会报错

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/回显.jpg)

​	如上，会输出我们括号里的内容，此时就成功的配置完了环境了，但是我们不能一直在黑色窗口编程，所以要安装ide



### 1、Pycharm

​	ide就是集成开发工具，Pycharm是一个很好的Python编程工具

​	[Download PyCharm: Python IDE for Professional Developers by JetBrains](https://www.jetbrains.com/pycharm/download/#section=windows)

​	点开如上网址，下载Community社区免费版即可，有能力的可以购买Professional或者自己去找激活key

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/downpycharm.jpg)

​	直接点，下载正常安装，这个没有什么特别注意的，无非就是关联py文件和添加右键打开项目创建桌面图标几个选择框英语， 可以自己视情况而定

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/4756750710efe4562c985522bdca4cd2.jpeg)

​	安装完成界面如下：

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/85276f483e381dd14d91846ef5acdad2.jpeg)

​	选择新项目

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/VeryCapture_20230622155945.jpg)

​	选择解释器，选择路径直接创建即可

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/image-20230622160034882.png)

​	进入插件商店，搜索Chinese，可以下载中文插件让IDE中文化





## 3、Python程序

​	我们看电影或者下载美女图片，要么就是：

- 一代宗师.mp4
- 刘亦菲.jpg

​	那么Python代码文件也有固定的后缀，是.py，告诉计算机这是一个Python代码文件

![](https://github.com/TuiYinMJ/180-Day-Python/blob/master/0%E3%80%8100%E5%A4%A9/pic/VeryCapture_20230622160456.gif)

​	我们首先新建一个目录用来存储python文件，避免代码多的时候混乱

```python
# coding:utf-8

print('Hello Python Course')
print('今天是2023年6月22日')
```

​	print是一个输出函数，也就是将()里的内容打印到屏幕上，第一行暂时不用管

​	编写完成后，我们可以用cmd切换目录到py文件代码目录，输入python python代码.py执行，一个py文件就是一个脚本文件

​	也可以在IDE的代码编写区域，右键-运行也可以



### 1、头部注释

```python
# coding:utf-8
```

​	也就是告诉Python解释器和系统一些规则，比如上面这一段，就是告诉编译器和系统我们的脚本编码格式



### 2、导入和注释

​	虽然现在接触导入有些早，但是这不是一个算很难的东西，所以提前了

```python
# coding:utf-8

import os  # 导入os模块

print(os.getcwd())  # 调用os模块中的getcwd函数
```

​	如上，就像有n个盒子，每个盒子都封闭着，我们想用一个盒子里的东西必须要先打开它，所以我们想用其他模块里的函数我们也要导入模块，否则无法使用，python自带内置的不用导入，比如print，而getcwd就是os模块中定义的一个获取当前目录的命令

​	注释就是给人看的，也就是以井号开头的内容，避免代码多了看不明白，#可以注释一行，还有多行注释

```python
"""
我被注释了
可以是多行
"""

'''
我也是
被注释了
'''
```

​	单引号或者三引号都可以



### 3、脚本入口

​	那么我们回家都要先开大门，再进客厅，再上电梯，再开卧室等等，我们不能翻墙而入或者凿墙而入

​	所以程序是不是也有一个必须的入口呢？

​	一般我们把代码执行的入口叫main

```python
if __name__ == '__main__':
    print('我是自己执行的啦')
```

​	如上，if是如果，后面会讲，现在先这样写，也先不用管两边的双下划线的含义

​	此时意思就是如果name == 'main'，则执行下面的代码，那么什么含义呢？

​	也就相当于在别人那里，他们叫你小黑，你自己叫你自己main，所以也就相当于一个里外的区别

​	如果name == main，那么就是自己执行自己，如果不等于main，那么就是被import导入执行的

​	我们也看到了，那个冒号不能丢，并且下一行print的开头有一个缩进，python用缩进来表示代码的层级关系

​	此时的print缩进了一级，也就就相当于是if name==main的子级语句，受它影响

​	若print和if在同一级，无缩进，那么就不会受到if语句的影响



​	但是这个入口不是必须的，我们不加也可以正常运行，大多数用来区分导入还是自运行和标志性的说一下这是个入口

```python
# coding:utf-8

print('Starting')

if __name__ == '__main__':
    print('main')
```

​	验证如上代码，并没有因为有name==main而先执行，而是Starting先输出了
