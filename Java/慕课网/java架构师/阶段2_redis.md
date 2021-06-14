# 阶段2_redis

## 分布式架构概述

分布式架构优点

- 业务解耦
- 系统模块化、可重用化
- 提升系统并发量
- 优化运维部署效率

分布式架构缺点

- 架构复杂
- 部署多个子系统复杂
- 系统之间通信耗时
- 新人融入团队缓慢
- 调试复杂

设计原则

- 异步解耦
- 幂等一致性
- 拆分原则
- 融合分布式中间件
- 容错高可用

## Redis

数据的屏障，保护数据库，提升数据库性能

### NoSql

#### 什么是nosql

- not only sql
- 传统项目使用纯数据库
- 为互联网和大数据而生
- 水平（横向）扩展方便高效
- 高性能读取
- 高可用
- 存数据，做缓存

#### 分类

- 键值对数据库,  Redis
- 列存储数据库，Cassandra
- 文档型数据库, MongoDB
- 图形数据库, Ne4J, FlockDB

### 分布式缓存

- 提升读取速度性能
- 分布式计算领域
- 为数据库降低查询压力
- 跨服务器缓存
- 内存式缓存

#### Redis

- NoSql
- 分布式缓存中间件
- Key-Value存储
- 提供海量数据存储访问
- 数据存储在内存里，读取更快
- 非关系型，分布式，开源，水平扩展

#### 缓存方案对比

memcache无法做数据持久化，存储的数据结构简单

redis优点

- 丰富的数据结构
- 持久化
- 主从同步，故障转移
- 内存数据库

redis缺点

- 单线程
- 单核

### redis安装

#### 核心配置 redis.conf

- dameonnize 前台后台
- dir 工作空间
- bind 远程访问
- requirepass 密码
- databases 16 默认16个库

#### redis_init_script

- 启动脚本
- pidfile, conf, redisport

#### 客户端工具使用

- redis-cli

#### 数据类型

##### string

- ttl过期时间
- Expire xxx 30
- set xxx valuexxx 20
- keys *
- get xxx
- append xxx value2
- strlen xxx
- incr xxx
- decr xxx
- clear
- incrby xxx 10
- desrby xxx 10
- getrange xxx start end
- setrange xxx 1 abc
- mset k1 aa k2 bb
- mget k1 k2
- msetnx k1 123 k3 cc.禁止重复
- select 1.切换库。默认是0
- select 0
- flushdb 清空库的内容

##### hash

- hset user name imooc
- hget user name

- hmset user age 18 sex man
- hmget user age sex name
- hgetall user
- hlen user
- hkeys user
- hvals user
- hincrby user age 3
- hincrbyfloat user age 2.2
- hexists user age
- hexists user email
- hdel user age

##### list

- lpush list1 pig cow sheep chicken
- lrange list1 0 -1
- rpush list2 x x x x
- lpop list1 拿掉以后就没有了
- rpop list1 
- llen list1
- lindex list1 2
- lrange list1 0 -1
- lset list1 1 1001
- linsert list1 before 1001 aaa
- lrem list1 2 aaa
- ltrim list1 1 2

##### set

- sadd set duck pig cow sheep sheep
- smembers set
- scard set
- sismember set pig
- srem set key
- spop set 2
- srandmembers ser1 3
- smove set1 set2 10
- set 差集，交集，并集
- sdiff set1 set2
- sinter set1 set2
- sunion set1 set2

##### zset

- zadd zset 10 duck 20 pig 30 sheep
- zrange zset 0 -1 withsorces
- zrank zset beef
- zrange zset 0 -1
- zscore zset beef
- zcard zset
- zrange zset 0 -1 withsores
- zcount zset 20 40
- zrangebyscore zset 20 40 withscores

redisdoc.com/index.html

## spring整合redis

### 多路复用，阻塞和非阻塞

多路复用，只负责接待，不做处理

### spring整合redis

redis desktop manager

redisOperator 工具类

jsonUtils.objectToJson 对象转json

## 发布和订阅

- subscribe food imooc-bigdata imooc-backend imooc-frontend
- publish imooc-backend java
- Psubscribe imooc*

## 持久化

RDB, AOF

### RDB

默认模式

dbfilename dump.rdb

数据的完整性会有问题

冷备份

### AOF

日志形式

appendonly yes

对实时性比较关心，用AOF

热备份

## 主从架构

slave提供读

master提供写

### 主从原理

初次是一个全量的数据同步

主从复制一定要开启master的持久化

### 主从模式

1主2从

vim redis.conf

info replication

### 无磁盘化复制

### 缓存过期机制

定期删除

惰性删除

## 哨兵模式

sentinel

sentinel.conf

master挂掉后，再恢复变成小弟

一主多从，主挂掉后就没法写入

哨兵监控，可以检测到挂掉的节点

哨兵一般是单数，便于监控那台挂了

选举leader

## Redis集群

修改redis.conf

redis-cli --cluster help  创建集群

redis-cil --cluster check xxx.xxx.xx.xx:6379

为master平均分配slots，16384

单机单示例VS哨兵模式VS集群模式

## 缓存穿透

查询的key在redis中不存在，对应的id在数据库也不存在，此时被非法用户进行攻击，大量的请求会直接打在db上，造成宕机，从而影响整个系统，这种现象称之为缓存穿透

解决方案：把空的数据也缓存起来，比如空字符串，空对象，空数组

## 布隆过滤器

## 缓存雪崩

成片的key都失效了，超大的流量，全部打在db上

### 雪崩预防

- 永不过期
- 过期时间错开
- 多缓存结合
- 采购第三方的redis

## 批量查询优化

mget

## pipeline批量查询优化

redisTemplate.executePipelined

管道

支持的类型更加丰富

