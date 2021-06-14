spring中的bean一定要通过容器去拿



获取应用上下文的四种方式：

ApplicationContextInitializer 容器创建完成之后的回调

ApplicationListener：观察者模式的应用



单例的bean无论获取多少个，都是同一个对象

自主制定的原型模式Bean



单例Bean的思考：

优势：

- 减少新生成实例的消耗
- 减少JVM垃圾回收
- 可以快速获取到Bean

劣势：

- 线程不安全

Spring设计默认单例Bean的理由

- 少创建实例
- 垃圾回收便捷
- 使用缓存快速获取

