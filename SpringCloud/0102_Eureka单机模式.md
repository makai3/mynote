## 1.建立eureka-server项目

打开`https://start.spring.io/`网站,在`Search for dependencies `输入框中输入`Eureka Server`,并选中.之后下载,并导入到ide中(sts同理)



## 2.添加注解

在主启动类上加上`@EnableEurekaServer`注解



## 3.添加配置

在`application.properties`中添加以下内容

```properties
spring.application.name=eureka-server
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
server.port=8761
```

关于配置的解释,我就不说了,后面参数详解中会讲的很细.最后一个是端口号

## 4.启动

主启动类右键-->run as--> Spring Boot App

等出现started之后,打开`http://localhost:8761/`网址,如果网页正常出现就算是成功了



## 5.测试

### 5.1 建立user-server项目

打开`https://start.spring.io/`网站,在`Search for dependencies `输入框中输入`Eureka Discovery`和`web`,并选中.之后下载,并导入到ide中(sts同理)

### 5.2 添加注解

在主启动类上加上`@EnableDiscoveryClient`注解

### 5.3 添加配置

```properties
spring.application.name=user-server
eureka.client.service-url.defaultZone=http://localhost:8761/eureka
eureka.instance.instance-id=${spring.cloud.client.ip-address}:${spring.application.name}:${server.port}
server.port=9001
```

### 5.4 添加个测试方法

启动类修改如下

```java
package com.makainb.user.server;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@EnableDiscoveryClient
@RestController
public class UserServerApplication {

	@Value("${server.port}")
	private int port;
	
	public static void main(String[] args) {
		SpringApplication.run(UserServerApplication.class, args);
	}
	
	@GetMapping
	public String getTime() {
		return String.format( "我是谁,我正在运行在%s端口上", port);
	}
}

```

运行成功后访问`http://localhost:9001`看看是否返回

### 5.5 建立user-client项目

打开`https://start.spring.io/`网站,在`Search for dependencies `输入框中输入`Eureka Discovery`和`web`,并选中.之后下载,并导入到ide中(sts同理)



### 5.6 添加注解

在主启动类上加上`@EnableDiscoveryClient`注解

### 5.3 添加配置

```properties
spring.application.name=user-client
eureka.client.service-url.defaultZone=http://localhost:8761/eureka
eureka.client.register-with-eureka=false
server.port=9002
```

### 5.4 添加个测试方法

启动类修改如下

```java
package com.makainb.user.client;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;

@SpringBootApplication
@RestController
@EnableDiscoveryClient
public class UserClientApplication {

	@Autowired
	private RestTemplate restTemplate;
	
	public static void main(String[] args) {
		SpringApplication.run(UserClientApplication.class, args);
	}
	
	@GetMapping
	public String getUser() {
		return restTemplate.getForEntity("http://user-server", String.class).getBody();
	}
	
	@Bean
	@LoadBalanced
	public RestTemplate restTemplate() {
		return new RestTemplate();
	}
}

```

运行成功后访问`http://localhost:9002`看看是否返回,如果成功返回,那么恭喜你,单机版的eureka就算是成功了.是不是很容易...前期不用太纠结各个配置的意思.可以实现功能就可以



[代码见资源](0102_Eureka单机模式.assets/20181002_sts.7z)