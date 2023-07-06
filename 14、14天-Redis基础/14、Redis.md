# 14、Redis

## 1、Redis简介

​	之前我们知道数据是保存到硬盘的，Redis用内存来保存数据，提高速度

​	但是内存很小，且关机后数据消失，但是这些数据也是从硬盘缓存过去的，所以完全不用担心丢失的问题

​	Redis基于key-value存储格式



​	**Windows安装方案：**

- windows版本维护网站：[GitHub - redis for windwos](https://github.com/tporadowski/redis)

​	因为redis官方维护的是Linux系统下的，这里只说一下win版本的，Linux自己百度，很容易

​	打开上面的网址下载后把路径添加到path环境变量

```
redis-server 启动redis服务器
redis-cli 启动redis命令行
```

​	顺序不能颠倒，否则无法使用



- 若不想使用绿色版，则参考官网利用WSL2安装方法

​	[Install Redis on Windows | Redis](https://redis.io/docs/getting-started/installation/install-redis-on-windows/)



## 2、Redis默认库

​	Redis默认16个逻辑库，从0-15

```mysql
select 0 -- 选择第一个逻辑库
set city JiNan -- 设置数据，key=city，value=JiNan
get city -- 获取数据
del city -- 删除数据
```

​	防止Redis服务器意外宕机丢失数据，提供了RDB和AOF持久化方式，RDB定期将内存数据同步到硬盘，AOF用日志方式



## 3、Redis数据类型

​	Redis是以key-value方式存储，key是字符串类型，而value需要根据情况设置类型，Redis的数据类型大致五种

- 字符串，通过 set key value 设置，get key获取，del key删除
  - **getrange key start end**，截取字符串内容，下标从0开始，包含尾
  - **strlen key**，获取字符串长度
  - **setex key sec value**，设置一个sec秒后过期，若毫秒级就用psetex
  - **mset key value key value**，设置多个key-value
  - **mget key key**，获取多个value
  - **append key value**，字符串结尾追加内容
  - **incr key**，数字自增1
  - **incrby key value**，数字加value
  - **incrbyfloat key value**，数字加value浮点
  - **decr key**，数字自减1
  - **decrby key value**，数字减去value
- 哈希，通过hset key field value设置，
  - **hmset key field value [field value...]**，设置多个field key
  - **hget key field**，获取哈希字段值
  - **hmget key field [field field...]**，获取多个
  - **hgetall key**，获取哈希表所有字段值
  - **hkeys key**，获取哈希表中所有字段名
  - **hlen key**，获取字段名个数
  - **hexists key field**，是否包含某个字段
  - **hvals key**，获取哈希表中所有字段值
  - **hdel key field**，删除哈希表字段
  - **hincrby key field value**，让某个字段值加上value
  - **hincrbyfloat key field value**，让某个字段加上value浮点
- 列表
  - **rpush key value [value...]**，列表右侧添加元素
  - **lpush key value [value...]**，列表作业添加元素
  - **lset key index value**，修改指定索引处的元素
  - **lrange key start end**，显示出start到end索引处的元素
  - **llen key**，获取列表长度
  - **lindex key index**，获取索引处元素
  - **linsert key [BEFORE/AFTER] pivot value**，向privot前面或者后面插入元素value
  - **lpop key**，删除key中最左侧的元素
  - **rpop key**，同上是右侧
  - **lrem key count value**，删除某个元素，count是删除第几个

- 集合
  - **sadd key value**，添加元素
  - **smembers key**，显示所有的value
  - **scard key**，获取集合长度
  - **sismember key value**，判断value是否存在于key中
  - **srem key value**，从key中删除value
  - **spop key**，随机删除并且返回集合的某个元素
  - **srandmember key count**，随机返回集合中的count个元素

- 有序集合
  - **zadd key score value**，添加value，并且给一个score，redis根据score排序
  - **zincrby key num value**，给某个value加上num
  - **zrevrange key start end**，比如zrevrange hello 0 -1，降序显示所有内容
  - **zrange key start end**，升序排列
  - **zcard key**，获取集合长度
  - **zcount key min max**，获取score在min和max之间的元素个数
  - **zscore key value**，获取某个value的score
  - **zrangebyscore key min max**，升序获取score在min和max之间的元素
  - **zrevrangebyscore key max min**，降序获取score在min和max之间的元素
  - **zrank key value**，获取value升序在key中排多少位
  - **zrevrank key value**，降序多少位
  - **zrem key value**，删除某个元素
  - **zremrangebyrank key start end**，删除排名区间内的元素
  - **zremrangebyscore key min max**，删除score在min和max区间的元素




- **flushdb**，清空库



## 4、Redis key命令

- **del key**，删除记录
- **exists key** ，判断key是否存在
- **expire key sec**，设置sec过期销毁
- **move key db**，将key移到其他逻辑库
- **rename key new**，修改名字
- **persist key**，移除过期时间



## 5、Redis 事务

​	还是，事务为了防止数据文件直接操作出现意外引发错乱

![image-20230706175841575](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307061758964.png)

​	也是一样的，只要事务不提交，就不会执行到数据库中

![image-20230706175931881](https://raw.githubusercontent.com/TuiYinMJ/Python-img/master/Python-img/202307061759928.png)

​	当我们exec执行后，就提交了

​	如果我们在提交过程中，被其他的客户端修改了，那么事务exec的时候机会失败，不会提交，watch就是监视

​	事务可以用discard取消事务，但是需要在提交之前



## 6、Redis 交互

​	首先安装redis模块

```python
import redis

if __name__ == '__main__':
    r = redis.Redis(host='localhost', port=6379, db=0)
    r.set('foo', 'bar')
    print(r.get('foo').decode('UTF-8'))
    del r
```

​	模块常用命令

- r.delete
- r.mset
- r.mget
- r.rpush
- r.lpop
- r.lrange
- r.sadd
- r.srem
- r.smembers
- r.zadd
- r.zincrby
- r.zrevrange

​	其实就和在dos中输入的都是一样的，不过是得从对象上引用



