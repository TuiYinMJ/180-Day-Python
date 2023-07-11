# 17、CSS基础

## 1、CSS基础

​	CSS层叠样式表，就是让我们的网页更加的好看

​	CSS分为：外部、内部、行内样式，只是引入方式不同，效果不影响

​	CSS且具有继承，也就是子元素会继承父元素的样式，自己有的话就用自己的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        h1{ /* 元素选择器，选中所有的h1*/
            color:red; /* 文本颜色 */
            font-size: 40px; /* 字体大小 */
        }
    </style>
</head>
<body>
    <h1>我的CSS样式</h1>
    <p>此处省略一千万字</p>
</body>
</html>
```

​	上面是一个内部样式，外部样式是通过link引入，行内样式是写在标签里，行内样式很少使用，往后用到了在说，这里暂且使用内部样式



### 1、选择器

​	学习CSS其实就是学习选择器，告诉浏览器，我们要给谁装饰，装饰什么效果而已

#### 1、标签选择器

​	标签选择器，也就是标签的名称，比如p{}、h1{}等等，但是这样选择范围比较广泛，会把所有的此类标签都选择

```css
h1{ /* 元素选择器，选中所有的h1*/
    color:red; /* 文本颜色 */
    font-size: 40px; /* 字体大小 */
}
```



#### 2、类选择器

​	每个标签都可以有一个class类目，将某些元素归为一类，类名是可以重复的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .desc{ /* 选中class为desc的 */
            color:green; /* 文本颜色 */
            font-weight: 700; /* 字体粗细 */
        }
    </style>
</head>
<body>
    <p class="desc">此处省略一千万字</p>
</body>
</html>
```



#### 3、背景样式

- background，聚合方式
- background-color，设置背景颜色
- background-image，设置背景图
- background-repeat，设置图片重复方向
- background-attachment，是否随着滚动条滚动
- background-position，背景图像的位置

​	这里使用css外部引入方式，先放html的代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./1.css">
</head>
<body>
    <h1>我的CSS样式</h1>
    <p class="desc">此处省略一千万字</p>
</body>
</html>
```

​	再来css代码，文件后缀名为.css

```css
.desc{
    color:green;
    font-weight: 700;
}

body{
    /* background-color: pink;
    background-image: url(https://img2.baidu.com/it/u=714264684,914065031&fm=253&fmt=auto&app=120&f=JPEG?w=992&h=437);
    background-repeat: no-repeat;
    background-position: center top; */

    background: pink url(https://img2.baidu.com/it/u=714264684,914065031&fm=253&fmt=auto&app=120&f=JPEG?w=992&h=437) no-repeat center top;
}
```

​	repeat就是一个平铺方向，具体的百度即可，不是很难的东西



### 2、常用样式

#### 1、文本样式

​	文本有个属性color。可以通过几种方式设置

- 颜色值：black、pink等
- 十六进制：#000000等
- rgb方式：rgb(0,0,0)
- rgba方式：rgba(0,0,0,0)，最后一个代表透明度，0为完全透明



- text-align，文本对其方式：center居中，left/right
- text-decoration，装饰，一般设置为none
- text-indent，首行缩进
- text-overflow，溢出内容显示方式：clip直接截断，ellipsis省略号
- text-shadow，文本阴影：x偏移,y偏移,模糊半径,颜色
- line-height，多行元素间的间距，行高
- letter-spacing，文本字符的水平间距
- text-transform，文本转换大小写capitalize，uppercase，lowercase等
- word-spacing，每个单词之间的距离
- white-space:nowrap，空白距离不换行

![行高](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307101751436.png)

​	两行文本基线的距离就是行高，底线到顶线的距离是行距，设置行高就是设置两条基线之间的距离，比如此时设置行高40px，字体大小20px，此时还剩下20px，上下平分，文本就处于居中了



#### 2、字体样式

- font-family，字体家族，通过先后顺序使用字体
- font-size，字体大小
- font-style，字体样式，下户线italic等
- font-weight，字体粗细，400默认，700加粗



#### 3、列表样式

- list-style，列表样式，通常none



## 2、伪类伪元素

### 1、伪类

​	伪类是添加到元素上的关键字，用于指定所选元素的特殊状态

- 元素:link，未访问的链接
- 元素:visited，访问的链接，用于超链接居多
- 元素:hover，鼠标悬浮，随意
- 元素:active，被激活，也就是按下鼠标的时候
- 元素:focus，拥有焦点的，常用于输入框



​	上面是一种状态伪类，也就是元素的状态，还有一种结构性伪类，选择哪些元素

- 元素:first-child，在一组兄弟元素中的第一个元素
- 元素:last-child，一组兄弟元素中的最后元素
- 元素:nth-child，选中某一个或者多个符合表达式的
- 元素:nth-last-child，和上面一样，但是从最后一个开始计算
- 元素:first-of-type，表示一组兄弟元素中其类型的第一个元素



### 2、伪元素

​	伪元素是一个附加至选择器末的关键词，允许你对被选择元素的特定部分修改样式

- ::after，在内容后插入新内容
- ::before，在内容前添加内容
- ::first-line，首行
- ::selection，被用户选中的部分
- ::first-letter，选择文本的第一个字符



## 3、选择器小结

​	通用的选择器：

- *，选择所有的元素，不管是什么
- 逗号，选中多个，比如p,h1，同时选中p和h1
- body h1，子孙后代选择器，body里的所有的h1
- body>h1，子选择器，只选择直属于body的h1元素
- h1+p，选择和h1平级的p元素，也就是兄弟选择器
- a[title]，属性选择器，选择a标签并且有属性title的
- .类名，类选择器，也就是标签中的class名
- #id名，通过id名称选择
- h1~p，选中h1后面的所有p兄弟标签



​	选择器优先级：

​	其实也就大概是选择的范围越小越精确，优先级越高

​	!important > 行内 > ID > 类 > 标签 > 通配符



​	有时候我们对元素需要进行设置，比如给行内元素设置宽高，但实际无法设置，需要通过display转换，元素类型分类：

- block：块元素，独占一行，宽高由内容撑起来，可设置宽高
- inline，行内，一行显示，宽高内容撑起，不可设置宽高
- inline-block，一行显示，宽高内容撑起，可以设置宽高
- none，隐藏元素



​	元素隐藏方法大全：

- display:none，隐藏元素不占用空间
- visibility:hidden，隐藏占据空间
- rgba，占用空间，取值可以全0也可以transparent
- opacity，元素透明，且继承，占用空间



​	元素中的内容超过了元素大小，称为溢出，我们可以根据需求隐藏元素

- overflow:visible，可见，不做任何处理，默认的
- overflow:hidden，隐藏溢出部分
- overflow:scroll，溢出与否都显示滚动条
- overflow:aotu，溢出滚动条，无溢出则没有



## 4、H5新增与其他补充

### 1、实体字符

​	在浏览器中，空格等无法被识别，若想输入多个或者显示字符需要用到实体字符

- \&nbsp; 空格
- \&gt; 大于
- \&lt; 小于

​	注意，这些是html的内容，不是使用在css中的



### 2、表单属性

- placeholder，输入框中的提示文本，得到焦点则消失
- autofocus，自动聚焦，打开网页焦点自动放到有这个属性的表单项上
- checked，默认选中单选或者复选框选项
- selected，默认选中下拉列表的某个选项
- maxlength/minlength，input的最小和最大输入长度
- readonly，只读，不可修改
- disabled，禁用，不能使用也不会提交到服务器



### 3、H5新增语义标签

- header，头部标签
- nav，导航
- section，文档某个区域的元素
- article，内容
- aside，侧边栏
- footer，底部

​	但是不常用，基本使用div



- audio，音频标签，属性为：
  - src：音频路径
  - controls，显示控制面板
  - muted，静音
  - autoplay，自动播放
  - loop，循环播放
  - preload，预加载
- video，视频标签，属性为：
  - src，同上
  - controls
  - muted
  - autoplay
  - preload
  - poster，视频封面
  - loop



### 4、布局标签

- div
  - div是一个块级元素，常用与包裹布局
- span
  - span是一个行内元素，常用与文本装饰等



## 5、盒模型

​	CSS处理网页，会认为所有的元素都在一个盒子里，每个能放元素的容器都可以叫盒子

​	就像日常生活里的盒子有：内容区、内边距、外边距、边框

​	边框、内容区、内边距会影响盒子的大小、外边距会影响盒子占用的空间大小

![img](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111629296.png)

​	宽高其实就是设置给内容区域的宽高



### 1、边框

​	边框也就是border，有上下左右四个，top、bottom、left、right

- border-width：边框宽度
- border-color：边框颜色
- boder-style：solid实线、dotted点线、dashed虚线、double双实线

​	border-radius，让边框四个角圆滑，上面的三个属性可以简写为border:xxx



### 2、内边距

​	padding，也分上下左右四个

- padding-top
- padding-right
- padding-left
- padding-bottom



### 3、外边距

​	margin，也分上下左右，行内元素设置margin无效

​	经常会用margin:0 auto

​	代表上下是0，左右是减去元素宽度，剩余两边平分



### 4、上下传递

![image-20230711164505842](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111645908.png)

​	如上，当一个块级包含子元素，子元素使用了margin-top，发现并不是子元素自己移动，而是把父元素拽着离顶部10px

​	解决这个问题很简单：

- 给父元素设置padding挤压子元素
- 父元素设置1px的border，颜色设置透明transparent
- 用overflow:auto触发BFC块级格式化上下文，相当于给某个盒子建立了一个独立空间
- 浮动子元素或者父元素



### 5、上下折叠

​	兄弟两个元素，一个margin-bottom，一个margin-top，造成边距折叠

![image-20230711165150069](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111651135.png)

​	此时会取一个较大的值，作为外边距，也就是并非30px的外边距，而是用较大的20



### 6、居中元素

![image-20230711165522899](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111655973.png)

​	尽量用flex居中，尽量不要用浮动或者text-align和margin的方式



### 7、外轮廓outline

​	outline在border的外面，不占据空间，使用方法和border一样

​	一般取值为outline-none，去掉聚焦的时候的轮廓



### 8、盒阴影

​	我们讲过文字阴影text-shadow，再来看下盒阴影box-shadow，一样的用法

![image-20230711165818737](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111658801.png)



### 9、怪异盒

​	我们正常盒模型也就是最上面所说的，设置宽高给内容区，若有padding和border等，还要更大

​	默认是content-box，怪异盒是border-box，边框盒子，设置的width和height是包含padding和border的，会内减

![image-20230711170206042](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111702108.png)

​	用box-sizing更改自己观察，想让哪个盒改为怪异盒就给谁加，星号是给所有的加

​	cursor是光标，point是小手形状，自己看吧



## 6、浮动

​	先了解一下默认的，normal flow，标准流按照顺序排列，不会出现层叠情况，也就是一层覆盖另一层的情况

​	若想脱离标准流，就可以用浮动、定位、flex等，实现脱标



### 1、基础

​	浮动起初是做文字环绕的，现在偶尔用来布局，基本都用flex，浮动后元素脱标，不占空间，后面的元素上移

- 向左或者向右浮动，元素会将自己的边界紧贴包含块（也就是父元素）或者其他浮动元素的边界
- 定位元素会层叠在浮动元素上面
- 浮动元素会互相跟随，无法实现层叠



### 2、水平间隙

​	行内级元素，会有一个水平间隙

![image-20230711171037807](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111710859.png)

​	如上，span是个行内级标签，hello和heihei之间很明显有个空白，解决方案有：

- 浮动flex，将两个元素浮动起来
- 删除回车，也就是让两个span在一行里
- flex布局
- 父元素设置font-size为0，然后给元素单独设置font-size大小



### 3、浮动练习

![image-20230711171622975](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111716067.png)

​	做一个百度的页码浮动练练手



### 4、margin负值

![image-20230711172149788](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111721860.png)

​	有5个元素，每个元素130px+10margin也就是140*5=700px

​	但是shoplist只有690px，也就是有一个元素肯定放不开，但是我们把这堆li放入一个box中，此时box被撑开是700px

​	然后给box设置一个负值右边距，700+-10px=690px，此时就可以将元素完整放入了



### 5、浮动高度塌陷

​	因为我们说过，浮动后元素不再占用空间，也就自然不会将高度给父元素汇报，此时父元素没设置宽高的话就会直接成为0*0，造成塌陷的状况

​	解决塌陷问题，叫做清除浮动，也就是清除浮动带来的影响

- 给父元素设置固定宽高，不推荐，因为我们有时候不知道要加多少东西
- clear清除，不推荐，会添加很多空元素，以后再讲其他的，先用这一种

![image-20230711173035693](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111730757.png)

​	如上，就是一个塌陷问题

![image-20230711173158004](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111731083.png)

​	如上，解决了塌陷问题，伪元素后必须要有content是个内容，不然不显示

​	clear的取值有：

- left
- right
- both，常用
- none默认



## 7、定位

​	定位用到position，取值为：

- static，静态，默认的
- **relative**，相对
- absolute，绝对
- **fixed**，固定
- stickey，粘性



### 1、相对定位

​	相对，也就是相对于一个元素，它的参照对象是自己原来的位置，相对定位不会脱离标准流

![image-20230711173806821](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111738886.png)



### 2、固定定位

​	固定定位会脱离标准流，相对于浏览器的视口，他不会随着浏览器太长滚动而滚动，也就是一直固定在某一个位置

![image-20230711174006417](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111740497.png)

​	浏览器显示内容的区域就是视口



### 3、绝对定位

​	绝对定位，脱离文档流，参照对象是相对于最近的非 static 定位祖先元素，没有的话就会去相对视口

​	它尝尝和相对定位成对出现，也就是父元素相对定位不移动，绝对定位元素相对于父元素进行位置调整



### 4、粘性定位

​	粘性定位是一个杂交结合体，它允许被定位的元素表现得像是一个相对定位，到了一定的阈值，就会表现为固定定位

​	比如商城的导航条

![image-20230711174737076](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111747154.png)

​	默认相对定位0,0，当滚动的时候就会根据相对它的最近滚动祖先0,0，不要听外面那些垃圾教材胡说八道说根据视口固定，那都瞎扯淡，这里要注意



### 5、z-index

​	z-index用来设置层叠顺序，只针对定位元素生效，取值可以是正负整数和0

​	也就是当元素重叠的时候，数值越大的越在上面，自己创建试一试，不讲了



### 6、定位居中元素

![image-20230711175418406](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307111754470.png)

​	就相当于，父元素宽度 - 子元素宽度 - left - right - margin-right - margin-left = 水平居中，垂直也一样





​	
