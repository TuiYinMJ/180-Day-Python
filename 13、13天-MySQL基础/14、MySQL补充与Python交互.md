# 14、MySQL补充与Python交互

## 1、MySQL事务

​	数据直接写入数据文件是很危险的，若是不直接写，而是通过缓存等再去同步，就可以多一步保障

​	默认情况，MySQL执行每条语句都会自动开启和提交事务

```mysql
START TRANSACTION; -- 开启事务
-- SQL语句
[COMMIT|ROLLBACK] -- 提交或者回滚，提交则就修改了，回滚则恢复到未修改状态
```



### 1、事务隔离级别

- read uncommitted 读取未提交的数据
- read committed 读取已提交的数据
- repeatable read 重复读取
- serializable 序列化

![image-20230704125248083](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307041252620.png)

​	如上图情况，A、B两人同时看到了有AB两个商家在售卖商品，且都是未售出状态，A抢先一步，购买了，但是还未提交事务，B一看未售出，也要去购买，A此时提交了事务，B购买失败回滚了，这种情况是不妙的

​	所以我们应该允许事务访问其他事务的临时状态，以免产生如上情况

```mysql
set session transaction isolation level 事务隔离级别; -- 当前会话就被修改为指定的隔离级别了
```

​	其他的隔离级别也一样，根据情况具体的修改

​	序列化隔离级别可以解决很多问题，但是并发性会大大的降低





## 2、Python交互Mysql

```python
import pymysql

config ={
    'host': 'localhost',
    'port':3306,
    'user': 'root',
    'password': 'root',
    'database': 'mytest'
}

if __name__ == '__main__':
    con = pymysql.connect(**config)
    sql = r'select * from hello'
    # 创建游标对象，可以用于执行SQL查询和获取结果
    cur = con.cursor()
    cur.execute(sql)
    print(cur.fetchall())
    cur.close()

```

​	使用到pymysql模块



