## Java线程安全

### 1. 用不好Synchronized关键字

 关于synchronize关键字你需要知道

- synchronize方法并不会被继承，需要在子类中重新指定
- synchronize究竟可以标注在哪里呢？方法声明、方法体
- synchronize它是怎么实现的呢
- jdk对synchronize做了优化。偏向锁，轻量级锁，重量级锁

 ### 2. 多线程下怎么更新变量值才好

常用的原子类

这一节好难

### 3. 阻塞队列

还是看不懂

### 4. 并不是什么时候都适合用copy-on-write

### 5. 对线程池的误区

