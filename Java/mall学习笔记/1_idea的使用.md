```
mvn package
jar tvf target/myproject-0.0.1-SNAPSHOT.jar
java -jar target/myproject-0.0.1-SNAPSHOT.jar
```

The `Greeting` object must be converted to JSON. Thanks to Spring’s HTTP message converter support, you need not do this conversion manually. Because [Jackson 2](https://wiki.fasterxml.com/JacksonHome) is on the classpath, Spring’s [`MappingJackson2HttpMessageConverter`](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/http/converter/json/MappingJackson2HttpMessageConverter.html) is automatically chosen to convert the `Greeting` instance to JSON.

parent：指定了包的版本

properties和yml没什么区别，可以直接把properties改成yml

spring-boot-configure-processor 生成自己的属性值

configuration MetaData

Spring Boot Actuator

springbootadmin

 easycode

