# 15、MongoDB

## 1、MongoDB 下载安装

下载地址：[Download MongoDB Community Server | MongoDB](https://www.mongodb.com/try/download/community)

MongoDB Shell也要单独下载了：[MongoDB Shell Download | MongoDB](https://www.mongodb.com/try/download/shell)

然后解压出来把MongoDB和MongoDB Shell的bin目录都加到path环境变量中，然后启动两个dos

第一个输入mongod启动服务器，第二个输入mongosh启动链接客户端

启动mongod的时候肯定会报错，因为没有要求的数据库目录文件夹

![image-20230706182242641](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307061822747.png)

然后从一堆输出里面找一下，找到报错的路径，按要求创建一个数据目录就行了

或者自己新建data/db文件夹，然后mongod -dbpath E:\mongodb\data\db，改成自己的路径就可以了

或者新建配置文件mongodb.conf

![image-20230707165121100](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307071651137.png)

如上，配置log文件和dbpath，然后再从终端mongod -f 配置文件的路径启动即可



## 2、简单使用MongoDB

- use mydb，如果有就使用这个逻辑库，没有就创建
- show dbs，查看已经存在逻辑库
- db，查看当前所在库
- db.mydb.insert({name:"cat",age:23,sex:"man"})，插入数据，mydb是自己的逻辑库名
- db.mydb.find()，查看逻辑库中的数据

​	注意，使用use创建逻辑库后用show dbs是看不到的，因为没有数据的库在MongoDB中没有价值，就不显示



## 3、MongoDB数据结构

​	是一个JSON格式，在MongoDB中叫BSON，被称作文档

​	某些BSON聚合在一起，就形成了集合

- db.dropDatabase()，在哪一个逻辑库中就删除哪一个逻辑库
- db.createCollection(“name”)，创建集合
- show collections，查看集合
- db.集合名.drop()，删除集合
- db.集合名.count()，查看集合记录数量
- db.集合名.dataSize()，保存集合数据所用空间
- db.集合名.renameCollection(“hh”)，重命名集合名称
- db.集合名称.insertOne({'name':'cat2','age':35}) #插入数据
- db.集合名称.insertMany([{'name':'db','age':21},{'name':'db1','age':22},{'name':'db2','age':23}]) # 插入多条



## 4、MongoDB主键值

​	在集合中，没有统一的字段约束，为了标识文档的唯一性，Mongodb为每个文档都添加了主键字段_id

![image-20230708154529878](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081545934.png)

​	如上，这个是具有唯一性且绝对不会重复的

![image-20230708154833224](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081548257.png)

​	ObjectID中包含了时间戳，所以我们可以提取记录保存的时间，但是这里的日期会转换成格林尼治时间，中国为东8区，所以要时间+8

​	回到我们上面，我们查看一个集合中的数据的时候用到find函数，若find参数为空，则无条件查询，若不为空，则有条件查询

![image-20230708155137433](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081551451.png)

​	取出name=hello的

![image-20230708155345828](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081553847.png)

​	取出name=hello的，并且年龄大于等于20的

- $lt，小于
- $gt，大于
- $lte，小于等于
- $gte，大于等于
- $in，包括
- $nin，不包括
- $ne，不等于
- $all，全部
- $not，取反
- $or，或
- $exists，是否含有某一个字段



## 5、分页查询

​	MongoDB大部分时候数据很多，一次性获取会死掉

​	我们此时就可以利用skip和limit分页查询

```
db.集合名.find().limit(2) 
db.集合名.find().skip(1).limit(2)
```

​	第一个是取出前2个，第二个是从第一条开始往后取2条

![image-20230708160200441](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081602467.png)

​	可以用sort排序，1代表升序，-1代表降序

![image-20230708160257001](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081602022.png)

​	根据age进行排序，升序排序



​	distinct去除重复

![image-20230708160456549](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081604569.png)

​	slice截取，

![image-20230708160631890](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081606905.png)

​	可以搭配使用



## 6、修改删除

- update
- updateMany

```
db.gg.updateMany({age:{$gte:20}},{$set:{name:'niubi2'}})
```

![image-20230708161045949](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081610973.png)

​	一个是条件，一个是把值设置成什么，update也一样的用法，只不过就是只能修改一条



- $unset，删除记录中的字段

```
db.gg.updateMany({},{$unset:{age:{$gte:18}}})
```

​	删除age大于等于18的，删除的是age属性

- $inc，对字段值做加法运算

```
db.gg.updateMany({},{$inc:{age:2}})
```

​	对每个age属性值加2

- $push，向数组属性添加元素
- $pull，删除数组属性的元素

```
db.gg.updateMany({name:'niubi2'},{$pull:{age:25}})
db.gg.updateMany({name:'niubi2'},{$push:{age:25}})
```

![image-20230708161710939](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081617962.png)

![image-20230708161733287](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081617310.png)



- remove删除记录

![image-20230708161849099](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307081618125.png)

​	不写条件，则删除所有的



## 7、数据索引

​	MongoDB存储大量数据，所以为了加快数据检索速度，需要为集合设置索引

```
db.集合名.createIndex({keys:1})
```

​	keys1升序，keys-1降序，但是这样会阻塞MongoDB，不推荐

```
db.gg.createIndex({age:1},{background:true})
```

​	这样就不会阻塞了，在后台空闲运行

```
db.gg.getIndexes()
```

​	获取所有索引



### 1、唯一性索引

​	唯一性索引只能创建在每个记录都含有的公共字段上，在非公共字段上是不能创建唯一性索引的

```
db.gg.createIndex({age:1},{background:true,unique:true})
```



## 8、Python交互

​	用到pymongo

```python
# coding:UTF-8

import pymongo

if __name__ == '__main__':
    client = pymongo.MongoClient(host='localhost', port=27017)
    client.hello.baga.insert_many([
        {'name': '张三', 'age': 27},
        {'name': '王五', 'age': 28},
    ])

    t = client.hello.baga.find({})
    for i in t:
        print(i)
```

​	插入与查询，其他的自己查阅



