## 阶段3_分布式搜索引擎

### 分布式搜索引擎

#### ES核心术语

索引index 表

文档document 行，以json形式存在

字段fields 列

映射 mapping 表结构定义

近实时NRT  Near real time

节点 node  每一个服务器

shard replica  数据分片与备份

分片（shard）：把索引库拆分为多份，分别放在不同的节点上，比如有3个节点，3个节点的所有数据内容加在一起是一个完整的索引库。分别保存到三个节点上水平扩展，提高吞吐量。

备份（replica）：每个shard的备份。

#### 倒排索引





#### 集成springboot

