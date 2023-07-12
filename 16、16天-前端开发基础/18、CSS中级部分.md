# 18、CSS中级

## 1、flex布局

​	flexbox，弹性盒模型

### 1、flex布局概念

- 开启了flex布局的元素叫：flex container
- flex container里的直接子元素叫flex item

![flexcontainer](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121417153.png)

​	flex item有以下特点：

- flex item受flex container的设置来进行控制和布局
- flex item不再严格区分块和行内级
- flex item默认包裹内容，但可以设置宽高

​	当display取值为flex或者inline-flex时，可以称为flex container



### 2、主轴交叉轴

![flexmodel](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121420061.webp)

​	如上图，整个大的叫flex container，其中的每个元素叫flex item

​	默认情况item根据主轴（main axis）方向排列

​	cross axis是交叉轴，main size是主轴宽度，cross size是交叉轴高度



### 3、flex属性

#### 1、flex container属性

- **flex-flow**，direction和wrap的简写
- **flex-direction**，主轴排列方向
  - **row**，默认从左到右
  - **row-reverse**，从右到左
  - **column**，垂直
  - **column-reverse**，从下到上
- **flex-wrap**，包裹元素是否换行
  - **wrap**，换行
  - **nowrap**，不换行，包裹不住了就压缩元素
  - **wrap-reverse**，反向换行
- **justify-content**，items在main axis上的排列方式
  - **flex-start**，与main start对齐
  - **flex-end**，与main end对齐
  - **center**，居中对齐
  - **space-between**
    - flex items之间的距离相等，与main start和main end两端对齐
    - 也就是两端各放一个元素，剩下的空间各个元素进行等分
  - **space-around**
    - flex items之间距离相等，flex items与main start和main end之间的距离是flex items之间距离的一半
    - 也就是等于两端start和end开始结束位置的空白距离等于flex items之间的一半
  - **space-evenly**
    - flex items之间距离相等，flex items与main start和main end之间的距离等于flex items之间的距离
    - 也就是flex items之间的间距等于两端start和end开始结束结束位置的空白距离

![justify](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121435985.png)



- **align-items**，items在cross axis上的排列方式
  - **center**，垂直居中
  - **flex-start**，与cross start对齐
  - **flex-end**，与end对齐
  - **baseline**，与基线对齐
  - **normal**，默认值。在弹性盒中，和stretch一样
  - **stretch**，当flex items在cross axis方向的height为auto时，会自动拉伸填充flex container
- **align-content**，items多行在cross axis上的排列方式
  - **flex-start**，与cross start对齐
  - **flex-end**，与end对齐
  - **center**，居中
  - **space-between**，同
  - **space-evenly**，同
  - **stretch**，没有高度的时候拉伸高度



#### 2、flex items属性

- **flex-grow**，决定items如何分布main axis上的剩余size，决定了flex-items如何扩展（拉伸/成长），默认值是0
  - **前提是flex container在main axis方向上有剩余的width时，flex-grow才会生效**
- **flex-basis**，用来设置items在main axis上的base size
  - 就是设置items的基础宽度，和width不同的是，当出现单词无法显示完整的时候，flex-basis会扩展size，一直到显示出所有的单词
  - **auto**，默认
  - 具体像素
- **flex-shrink**，让items压缩体积，取值为数值，决定了flex-items如何收缩（缩小），默认值是1
  - 满1行的时候是否希望压缩元素的体积，就要用flex-shrink
- **order**，items的排列先后顺序
  - 数字越小排列越靠前
- **align-self**，设置某一个item在cross axis上的对齐方式，和align-items效果一致
  - **auto**，默认，遵从flex container的align-items设置
  - **stretch**
  - **flex-start**
  - **flex-end**
  - **center**
  - **baseline**

- **flex**，简写
  - flex-grow、flex-shrink、flex-basis的缩写属性



#### 3、flex布局问题

![image-20230712144522644](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121445709.png)

​	当一行排列不下，并且不想让space-between两侧居中的时候，就加i或者spsan空元素，在flex中不严格区分行内和块级，设置宽度将原来的元素挤过去，添加空元素的个数是列数-1个或者-2个



## 2、动画位移

### 1、transform形变

​	transform可以对某个元素进行某些形变，比如：旋转、缩放、倾斜或者平移等等

​	行内元素通常不能进行形变

​	常见的使用函数如下：

- **translate**(x,y)，水平移动，也可以使用百分比，百分比相对于自身的宽高，也可以分别写为translateX()等
- **scale**(x,y)，缩放，也可以取值百分比，大于1放大，1不变，小于1缩小
- **rotate**(deg)，旋转，正数顺时针选中，负数逆时针旋转
  - 默认原点在center中心，旋转和缩放的就默认根据中心，可以使用origin改变圆心位置origin(x,y)，可以用上下左右的英文单词，也可以用具体的像素
- **skew**(deg,deg)，倾斜，自己尝试

​	transform可以一次性加上面4种，不用一行一行的写，用空格分开就行



### 2、居中总结

#### 1、水平居中

- 行内元素：给父元素设置text-align:center
- 块元素：设置margin:0 auto
- 绝对定位：left0 right 0 margin:0 auto
- flex布局：justify-content:center



#### 2、垂直居中

- 绝对定位：top0 bottom0 margin:auto 0
- flex布局：align-items:center
- top和translate，top移动父元素的50%，translate移动自己的-50%



### 3、transition过渡

​	transition是css提供的一种在修改css属性时控制动画速度的方法，也就是让属性的变化持续一段时间，而并非立刻完成

​	并非所有css属性都支持tansition，可在[developer.mozilla.org](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_animated_properties)进行详细的查询



#### 1、属性和使用

​	tansition是transition-property（给谁加过度）、transition-duration（持续多久）、transition-timing-function（持续曲线）、transition-delay（延迟多久开始）总结合体



​	transition-property取值：

- none，都不执行动画
- all，都执行动画
- css属性名，给指定的css属性执行



​	transition-duration取值：

- s或者ms



​	transition-delay：

- s或者ms



​	一般简写：transition：all s



​	执行曲线：

![image-20230712150145289](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121501328.png)





### 4、Animation

​	使用步骤分为两步：

1. 使用keyframes定义动画序列
2. 配置动画执行的名称、持续时间、动画曲线、延迟、执行次数、方向等

![image-20230712150312537](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121503593.png)

​	动画的使用如上

- **animation-name**:动画名; /* 执行哪个动画 */
  **animation-duration**:时间; /* 动画执行多久 */
  animation-timing-function:属性; /* 执行曲线 */
  animation-delay:时间; /* 延迟 */
  **animation-iteration-count**:; /* 动画执行次数 取整数数值 */
  animation-derection:; /* 动画执行方向 可取值normar和reverse */
  animation-fill-mode:; /* 停留位置，normar，forwards，backwards */
  animation-play-state:; /* paused暂停  */

​	常用的一些属性，次数可以取值为infinite，无限循环



## 3、vertical-align

​	行盒：每一行都有一个行盒，它的作用就是要包裹所有的内容

​	元素的高度由所有行盒的总高度撑起，如果行盒内包裹多个内容，如何对齐？如果胡乱摆放，网页不美观，所以为了对齐，此时就要用到vertical-align

​	vertical-align就是影响**一个行盒中行内级元素的垂直方向的位置**

​	一个div不设置高度的时候，由内容撑起来，撑起来的本质就是内容有行高，行高为何能撑起高度，是因为行盒要包裹一行内所有的内容

​	当inline-block没有内容时，底部作为基线，有内容时，内容中最后一行文本的基线作为对齐



​	**line boxes如何包裹？**

- 只有文本则包裹文本
- 有图片有文字则都包裹
- 有图片，有文本，有inline block则全部包裹



### 1、baseline

​	line-boxes一定会想办法包裹住当前行中所有的内容，vertical-align是有默认值的，也就是baseline，是基线对齐的

​	即使div里面只有一个img，也会预留空白，防止以后突然插入文本，所以要确保输入文本也是基线对齐，所以要留白



### 2、取消基线

```css
vertical-align:top; /* 顶部对齐 */
vertical-align:middle; /* 中线对齐 */
vertical-align:bottom; /* 底部对齐 */
```



​	vertical-align不是给父盒子设置，是给行内级的元素上设置的

​	top是顶部，bottom是底部

​	但是middle不是居中，middle是行内级盒子的中心点与当前父行盒的基线加上x高度的一半进行对齐的，**也就是和x的中线进行对齐**

![对齐](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307121509829.png)

​	如上图，文字都会进行下沉处理，也就是x的中心可能并非正好卡在正中间，所以就会造成用行内级的元素中心去对x的中线，形成上大下小



## 4、其他补充

### 1、CSS代码编写顺序

1. 定位position和布局代码
2. 展示display和可见visibility
3. 盒子模型margin border等
4. 字体和文本属性
5. 背景相关等装饰
6. 位移过度等动画



### 2、CSS补充属性

​	gradient，渐变：

```css
background-imgage:linear-gradient(red,blue);
/*默认从上到下，可以改变方向，如下*/
background-imgage:linear-gradient(to right,red,blue);
background-imgage:linear-gradient(to right top,red,blue);
background-imgage:linear-gradient(45deg,red,blue);
```

- linear-gradient()，线性渐变
- radial-gradient()，以圆点散开渐变
- repeating-linear-gradient()
- repeating-radial-gradient()





​	blur（模糊半径），模糊半径越大，图片越模糊，通常和**filter**和**backdrop-filter**搭配使用

- Filter作用于当前元素且后代也会继承
- backdrop-filter作用于元素背后的所有元素

```css
filter: blur(5px);
backdrop-filter:blur(5px);
```





​	calc计算，运算符两侧要有空格

```css
        .item1{
            width: calc(100% - 100px);
            background-color: #f00;
        }
```





​	var变量，只有后代元素可以使用

```css
html{
    --main-color:red;
}

.main{
    color:var(--main-color);
}
```





​	css常见单位

​	之间我们常用的就是px

​	单位可以整体分为两类：

- **绝对长度单位**，设置固定的大小，不相对于其他东西
  - 唯一一个经常使用的就是**px**
- **相对长度单位**，相对于其他一些东西设置自己的大小
  - **em**：相对于自己的font-size大小
  - **rem**：相对于根元素的字体大小
  - **1vw**：视口宽度的1%，前面的数字是几就是百分之几
  - **1vh**：视口高度的1%，前面的数字是几就是百分之几



