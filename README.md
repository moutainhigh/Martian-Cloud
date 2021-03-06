<div align=center>
<img width="200px;" src="http://mars-framework.com/img/logo-github.png"/>
</div>

<br/>

<div align=center>

<img src="https://img.shields.io/badge/licenes-MIT-brightgreen.svg"/>
<img src="https://img.shields.io/badge/jdk-1.8+-brightgreen.svg"/>
<img src="https://img.shields.io/badge/maven-3.5.4+-brightgreen.svg"/>
<img src="https://img.shields.io/badge/release-master-brightgreen.svg"/>

</div>

<br/>

<div align=center>

Martian 框架的官方分布式组件

</div>

## 项目简介

Martian-cloud 是Martian的官方分布式组件

服务之间的通话采用Rest风格，以Zookeeper为注册中心，并且对Martian的入侵很小

## 仅需一个依赖

```xml
<dependency>
    <groupId>com.github.yuyenews</groupId>
    <artifactId>mars-cloud-starter</artifactId>
    <version>最新版，具体看《组件介绍》</version>
</dependency>
```

## 支持Feign调用
```java
/* 
这个注解的serverName跟你要调用的那个服务的name一致（配置类里cloud配置的name） 
beanName 不写的话，默认为类名首字母小写
*/
@MarsFeign(serverName="mars-demo",beanName="demoFeign")
public interface DemoFeign {
    /* 
        这里面的所有方法，跟你要调用的那个API中的方法名一致
    */
    返回类型 insert(DemoEntity entity);

    /*
        可以用@MarsContentType注解 来指定本次请求的ContentType
    */
    @MarsContentType(ContentType = ContentType.JSON)
    返回类型 selectList(DemoEntity entity);
}
```

## 也支持RestTemplate

```java
返回类型 result = MarsRestTemplate.request(服务name,MarsApi接口的方法名,new Object[]{参数对象1，参数对象2},返回类型.class, ContentType.FORM);
```