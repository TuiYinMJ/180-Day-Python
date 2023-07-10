# 16、HTML基础

## 1、HTML基础

​	HTML是一个超文本标记语言，学习的也就是一些标签组合起来，很容易掌握记忆

​	浏览器可以选择：Google Chrome、Edge、Firfox

​	开发IDE选择：Visual Studio Code、Sublime text



### 1、HTML简介

​	超文本，自然就不只文本，比如图片、视频、音乐等等

​	和py一样，html代码的文件需要为.html后缀

```html
<!DOCTYPE html> <!-- 声明文档类型 -->
<html lang="en"> <!-- 根标签 -->
<head> <!-- 头部，对网页进行一些说明 -->
    <meta charset="UTF-8"> <!-- 元标签设置网页编码 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- 元标签设置适应兼容 -->
    <title>Document</title> <!-- 网站的标题 -->
</head>
<body> <!-- 在网页上所看到的内容 -->
    这是我的第一个网站 <!-- 我们网站的显示内容 -->
</body>
</html>
```

​	上面这是一个基本的文件结构，所有绿色的单词加上两端的尖括号就是一个标记，每个标记有不同的含义



### 2、常用标签

- p，段落标签，定义文章的一个段落
- h，标题标签，定义文章标题，h1~h6

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>2023年7月9日山东济南发生这件大事</h1>
    <p>文章1</p>
    <p>文章2</p>
</body>
</html>
```



- img，图片标签
  - src属性为图片来源
  - alt属性为图片加载失败的文字提示
- a，超链接
  - href为跳转地址
  - target以什么方式跳转
    - _self为本页面跳转
    - _blank为新页面跳转
- ul ol li，列表
  - ul为无序列表
  - ol为有序列表

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <img src="https://img2.baidu.com/it/u=3994011889,129872026&fm=253&fmt=auto&app=138&f=JPEG?w=846&h=500" alt="图片失败显示的文字">
    <a href="https://www.baidu.com/" target="_self">点我跳转到百度</a>
    <h1>我的技能有</h1>
    <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>Javascript</li>
        <li>C/C++</li>
        <li>Python</li>
        <li>Mysql/Redis/MongoDB</li>
    </ul>

    <p>感谢以下朋友对我的赞助，排名不分先后</p>
    <ol>
        <li>张三</li>
        <li>李四</li>
        <li>王二麻子</li>
    </ol>
</body>
</html>
```

#### iframe标签
iframe就是从网页中嵌入另一个网页

```html
<iframe src="https://www.baidu.com" width="500px" height="500px" frameborder="0"></iframe>
```

freamborder为0无边框，1有边框



### 3、表格标签

​	表格就像Excel表格一样

- table，表格大标签
- caption，表格标题
- tr，行
- th，表头单元格
- td，单元格
- thead，表格头部，提高阅读性
- tbody，表格主体
- tfoot，表格结尾

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <table width="400px" border="1px solid black">
        <caption>2023.07.09商品库存</caption>
        <thead>
            <tr>
                <th>ID</th>
                <th>商品名</th>
                <th>库存</th>
            </tr>
        </thead>
        <tbody align="center">
            <tr>
                <td>1</td>
                <td>鸡蛋</td>
                <td>3000</td>
            </tr>
            <tr>
                <td>2</td>
                <td>车厘子</td>
                <td>5</td>
            </tr>
            <tr>
                <td>3</td>
                <td>牛奶</td>
                <td>10000</td>
            </tr>
        </tbody>
        <tfoot>
            <tr>
                <td colspan="3">备注：</td>
            </tr>
        </tfoot>
    </table>
</body>
</html>
```

 属性讲解：

- width，表格宽度
- boder，表格边框，参数为：宽度，样式，颜色
- align，对齐方式
- colspan，列合并
- rowspan，行合并



### 4、表单

​	网页中提交数据的东西就是表单了

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form action="提交地址" method="提交方式"> <!-- action后台提交地址,method分为get和post提交 -->
        姓名：<input type="text" name="name"> <!-- input输入框，根据type不同展现不同形式,name必须有 -->
        <br> <!-- br是换行 -->
        密码：<input typr="password" name="pwd">
		<!-- name是往后台提交的时候的属性值，比如百度的时候www.baidu.com/?wd=,wd就是个name，没有name后台不知道提交的是哪一个的属性值 -->
        
        <br>
        性别：
        <label for="man"> <!-- label提高交互，for通过id绑定，点击男也会选中，否则只能点单选框 -->
            <input type="radio" name="sex" value="man" id="man">男 <!-- value必须有，后台只能读取value值，无法读取字体内容，sex是分组，性别组是一组，不然没法实现单选，radio就是单选了 -->
        </label>
        <label><input type="radio" name="sex" value="woman">女</label>
        <!-- 也可以直接用label包括，简单点 -->

        <br>
        爱好：
        <label><input type="checkbox" name="aihao" value="xiyan">抽烟</label>
        <label><input type="checkbox" name="aihao" value="chang">唱</label>
        <label><input type="checkbox" name="aihao" value="tiao">跳</label>
        <label><input type="checkbox" name="aihao" value="rap">RAP</label>
        <label><input type="checkbox" name="aihao" value="lanq">篮球</label>
        <!-- checkbox为多选，也必须要有value，name是分组，这个分组中选出爱好这样 -->

        <br>
        出生地：
        <!-- select和option为选择框 -->
        <select name="csd">
            <option value="sd">山东</option>
            <option value="hn">河南</option>
            <option value="js">江苏</option>
        </select>

        <br>
        个性介绍：<br>
        <!-- textarea文本域，也就是大的文本框 -->
        <textarea name="gxjs" cols="30" rows="10"></textarea>

        <br>上传个人简历：<input type="file">
        <!-- file为上传文件那种 -->

        <br>
        <input type="submit">
        <!-- submit是提交按钮，value可以改变按钮的标题 -->
    </form>
</body>
</html>
```



自己利用所学标签，制作一个简单的注册页面，随便找个网站按照他们的排版抄就可以了



