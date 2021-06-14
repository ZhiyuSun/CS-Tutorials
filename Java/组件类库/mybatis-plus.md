# MyBatis-Plus

## 快速入门

### MyBatis vs JPA

#### mybatis

优势

- SQL语句可以自由控制，更灵活，性能较高
- SQL与代码分离，易于阅读和维护
- 提供XML标签，支持编写动态SQL语句

劣势

- 简单CRUD操作还得写SQL语句
- XML中有大量的SQL要维护
- MyBatis自身功能很有限，但支持Plugin

#### JPA

优势

- JPA移植性比较好
- 提欧共了很多CRUD方法，开发效率高
- 对象化程度更高

### MyBatis-Plus简介

MP是一个MyBatis的增强工具，只做增强不做改变

#### 特性

- 无侵入、损耗小、强大的CRUD操作
- 支持lamdba形式调用，支持多种数据库
- 支持主键自动生成，支持ActiveRecord模式
- 支持自定义全局通用操作，支持关键词自动转义
- 内置代码生成器，内置分页插件，内置性能分析插件
- 内置全局拦截插件、内置Sql注入剥离器

## 基本使用

@TableId 确定主键

@TableField("name") 设置字段名称

数据表中不存在的字段

- private static String remark
- private trasparent String remark
- @TableField(exist=False)

可设置日志级别为trace

## MyBatis-plus查询方法

条件查询器

selectById——id=

selectBatchIds——in

selectByMap——name=xx and age = xx，键是数据库中的列名

selectList & queryWrapper——包含什么，小于什么，不为空like, likeRight, isNotNull or ge orderByDesc, orderByAsc, apply 可使用函数，inSql 级联查询

指定字段

queryWrapper.select("id", "name")







