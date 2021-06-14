## web开发模式

servlet+jsp+javaBean

1. 使用servlet处理用户的请求
2. jsp显示数据
3. javaBean封装和处理数据

过滤器

监听器

## spring

底层实现原理

### IOC

将对象的创建权交给工厂

xml里面，bean里面设置property

#### 三种实例化Bean的方式

- 使用类构造器实例化（默认无参数）
- 使用静态工厂方法实例化（简单工厂模式）
  - factory-method
- 使用实例工厂方法实例化（工厂方法模式）
  - factory-bean, factory-method
- 一般情况下都是第一种，如果这个类的构造复杂，用二三种

#### Bean的配置

作用域：singleton, prototype

#### 生命周期

init-method, destroy-method

详细的生命周期有很多，详见ppt

beanpostprocessor的作用，见视频3-8

### spring的属性注入

对于类成语变量，注入方式有三种：

- 构造函数注入
  - contructor-arg
- 属性set注入
  - 开发中更习惯用set方法注入
  - 使用property
  - 值用value，对象用ref
- 接口注入

spring支持前两种

复杂类型的注入

### sping的bean管理注解

@component 相当于 id

@reposity等

@Resource = @Autowired + @Quilified

@scope

@postConstruct

@preDestroy

### AOP

#### 定义

采用横向抽取机制，取代了传统纵向继承体系重复性代码（性能监视、事务管理、安全检查、缓存）

使用纯Java实现，不需要专门的编译过程和类加载器，在运行期通过代理方式向目标类织入增强代码

#### 术语

图

#### 底层实现

#### 代理知识总结

#### AOP增强类型

### 基于Aspectj的开发

### JDBC

jdbc tempalate提供统一的模板方法，在保留代码灵活性的基础上，尽量减少持久化代码

优点：

- 简单，灵活

缺点：

- sql与java代码参杂
- 功能不丰富

课程总结

- 持久化操作特点
  - 必须
  - 机械性
- ORM
  - 对象-关系
- JDBC tempalte是spring框架对jdbc操作的封装，简单、灵活但不够强大
- 实际应用中还需要和其他ORM框架混合使用

## spring MVC

### 基本操作

#### 定义

spring框架的一个后续产品

spring框架的一个子模块，二者可以很好的结合使用，不需要整合

#### 核心组件

- DispatcherServlet：前置控制器
- HandlerMapping：将请求映射到Handler
- Handler：后端控制器，完成具体的业务逻辑
- HandlerInterceptor：处理器拦截器
- HandlerExcutionChain：处理器适配器
- ModelAndView：装载模型数据和视图信息
- ViewResolver：视图解析器

#### 实现流程

1. 客户端请求被DispatcherServlet接收
2. DispatcherServlet将请求映射到Handler
3. 生成Handler以及HandlerInterceptor
4. 返回HandlerInterceptor（Handler+HandlerInterceptor）
5. DispatcherServlet通过HandlerAdapter执行Handler
6. 返回一个ModelAndView
7. DispatcherServlet通过ViewResolver进行解析
8. 返回填充了模型数据的View，响应给客户端

大部分组件由框架提供，开发者只需要通过配置进行关联。开发者只需手动编写Handler,View

#### 基于注解开发

@Controller,@RequestMapping

三种方式传值，modelAndView, map，string

### 数据绑定

将HTTP请求中的参数绑定到Handler业务方法的形参

@ResbonseBody,@RequestParam

### restful

资源的表述，状态转移

- 统一了客户端访问资源的接口
- url更加简洁，易于理解，便于扩展
- 有利于不同系统之间的资源共享

### 拦截器

2-3 三种核心配置文件的配置方式，原理讲的很棒

- 拦截器是使用JDK动态代理实现的，拦截的是对应调用方法的拦截
- 过滤器是使用Filter实现的，拦截的是request对象

### SSM整合案例

可以有多个module



## 注意点

maven项目，webapp模板

java要标记为source root

xml怎么把提示给弄出来

## 经验点

- 一般把src/main/java设置为sourceRoot



## 问题

- HttpSession session, session.setAttribute("session_user", user), session.getAttribute("session_user)
- 

