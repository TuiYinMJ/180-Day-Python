# JavaScript

## 1、使用方法

​	使用script标签，在HTML页面中插入

​	script标签在head中引入外部文件，后缀为js

![image-20230713161606099](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131616447.png)

​	alert，弹出一个对话框，js的内置函数



## 2、变量

​	变量和其他的语言一样，用来临时存储信息的，js中也没有严格类型区分，也就是不用说变量是什么类型的，但是赋值的时候是有数据类型的

​	变量声明有两个方式：`let`和`var`

​	首先说一下不同之处：

- var会存在变量提升，let不会
- var可以声明多次同一个变量，let不行
- var是全局的，let是块级的，也就是只在当前代码块有用
- 建议使用let

![image-20230713162516241](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131625282.png)

​	自己把var换成let试试，直接报错，console.log()是从调试工具信息，按F12就可以打开网页调试工具



## 3、自定义函数

​	函数也一样，为了完成某一段代码的复用，方便维护和管理

![image-20230713162857893](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131628934.png)

​	一个简单的函数的创建和调用，和Python差不多，不过用到了花括号

​	形参和实参忘了Python介绍没介绍了，形参就是函数的参数列表没有实体值占位的，add(1,2)传入的就是实参

![image-20230713163105916](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131631953.png)

​	函数也可以有返回值

```javascript
let mad = function add(x, y) {
	return x + y
}

let num = mad(1, 2)
alert(num)
```

​	还有上面这种函数定义方式，效果都是一样的



## 4、数据类型

- number，数字类型
- string，字符串
- boolean，布尔
- undefined，未定义，未赋值的
- null，空对象
- object，对象
- NaN，number的特殊形式，是数字false，不是数字true

​	虽然定义变量不用数据类型，但是数据是有类型的

- parseint()，转为整数
- parseFloat()，转为浮点
- Number，转为数字
- Boolean，转为布尔

![image-20230713164211912](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131642945.png)

​	其他的自己尝试，isNaN是不是数字，也不能倒翻天罡，汉字转number肯定不行

```javascript
let str1 = '123'
let str2 = '123'
console.log(str1 === str2);
console.log(str1 !== str2);
```

​	其他的运算符没啥可讲的，就说这一个===和!=\=，在js中\==和!=只会判断值是否相等，不会判断类型

​	但是===和!\=\=\=不光判断值还判断类型是否相等



## 5、流程控制

​	和Python一样的，也是让代码根据条件来怎么执行代码

![image-20230713165611624](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131656668.png)

​	和Python差不多的

![image-20230713171342466](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131713501.png)

​	Switch case，就是Python里的match那个

![image-20230713171501112](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131715148.png)

​	for循环

![image-20230713171546702](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131715733.png)

​	while循环，break跳出循环，continue结束本次循环开始下一次，和Python一样

![image-20230713171711510](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307131717538.png)

​	do while是先执行一次再判断



## 6、常用内置函数

### 1、字符函数

- str.substr(start,要提取字符数量)，截取字符串，提几个
- str.substring(start,end)，截取字符串，含头不含尾，截取start-end区间
- str.charAt(index)，用于获取字符串中指定索引位置的字符
- str.split()，拆分字符串返回列表
- str.length()，字符串长度
- str.indexOf()，在字符串中查找指定子字符串的第一个出现位置的索引，第二个参数可以设置从第几个位置开始找，区分大小写
- str.toLowerCase()，转小写
- str.toUpperCase()，转大写
- str.concat()，拼接多个字符串
- str.replace()，替换文本



### 2、日期函数

![image-20230714151142782](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141511890.png)

​	new Date创建一个表示当前日期和时间的对象，传参可以创建一个特定日期的日期时间对象

​	利用取各个部分的内容，写一个函数，让传入的时间按照2023-07-14 15:13:52的格式输出

![image-20230714151845919](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141518955.png)

​	代码如上，别照抄，思考一定要



### 3、数学函数

![image-20230714152451204](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141524235.png)

​	如上，自己练习



## 7、数组

```javascript
//let arrobj = new Array(); // 声明创建一个不指定长度的数组，实例化创建
//let arrobj = new Array(5); // 声明创建一个指定长度的数组
//let arrobj = new Array(5，6,7,8,9,10,11,12); // 声明创建一个带有默认值的
let arrobj = [5，6,7,8,9,10,11,12]; // 简单的创建赋值最简单的方式了
```

![image-20230714153119528](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141531566.png)

​	遍历和访问方式，自己练习



## 8、DOM操控表单

​	表单主要作用就是客户端接收用户信息，然后将数据给后台的程序操控

​	JS主要就用来获取和设置各种表单元素

![image-20230714154636126](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141546169.png)

​	通过元素id获取元素对象，并且设置值，且绑定事件函数

![image-20230714155307880](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141553917.png)

​	通过name属性获取一些元素

![image-20230714160713050](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141607096.png)

​	节省代码量，不用一个个的创建选择项，Option的两个参数第一个为显示的值，第二个为选择的值，也就是提交给服务器的value

![image-20230714163051568](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141630637.png)

​	自己参悟

![image-20230714170544378](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307141705431.png)

​	按钮效果，自己参悟



## 9、常用事件

- onclick，单机
- ondblclick，双击
- onmouseover，鼠标移动到一个元素上方
- onmouseout，从一个元素上移出
- onmousedown，鼠标按钮被按下
- onkeydown，按下任意键
- onkeyup，抬起任意键
- keypress，按下并释放任意键
- onfoucs，焦点
- onblur，失去焦点
- onsubmit，提交
- onchange，修改



还有getElementsByTagName和getElementsByClassName没讲，自己看



# JQuery

​	JQuery是JavaScript的一个工具库，能更方便的编写代码等

​	[Microsoft Ajax Content Delivery Network Assets | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/ajax/cdn/overview#jQuery_Releases_on_the_CDN_0)

​	上面是一个微软上托管的在线JQuery CDN服务器，可以让我们不下载JQuery使用

![image-20230720163905021](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307201639112.png)

​	导入如上，我们开始用JQuery操作网页看看多容易



## 1、JQuery操作DOM

![image-20230720165010028](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307201650060.png)

​	获取元素内容

​	还有属性选择器：

- $("[href]")，带有href属性的元素

​	以及css选择器

- $("p").css("color","red")，选中p标签，并且把颜色改为红色

![image-20230722123110305](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307221231380.png)

​	它还有很多事件，ready是所要执行的代码在DOM元素被加载完成的情况下执行，和onload差不多，但是onload是在页面加载完发生，也就是DOM和其他页面元素，所以ready比onload快一些

​	hide隐藏了p标签元素，相反show是显示，也可以用toggle，click一样，也是被单机

​	jquery事件参考手册：[jQuery 参考手册 - 事件 (w3school.com.cn)](https://www.w3school.com.cn/jquery/jquery_ref_events.asp)

​	其他的自己找手册和网站看吧，很容易，主要就是给爬虫做铺垫，不做专业前端开发
