---
title: SpringBoot起步依赖
date: 2022-10-03
comments: false
categories: [Java, SpringBoot]
tags:
  - Java
  - SpringBoot
---

## 起步依赖

创建Spring Boot项目非常简单，使用Maven管理项目只需要在POM文件中继承 `spring-boot-starter-parent` 即可。

`spring-boot-starter-parent` 中定义了各种技术的默认配置，大大简化了我们开发所需要进行的配置。

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.7.4</version>
</parent>
```

## 依赖管理

查看 `spring-boot-starter-parent` 的源代码，能够发现它还继承至 `spring-boot-dependencies` 

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-dependencies</artifactId>
    <version>2.7.4</version>
</parent>
```

继续查看 `spring-boot-dependencies` 源代码，内部通过 `dependencyManagement` 管理各种项目依赖，同时使用 `properties` 标签来锁定这些依赖的版本号信息

```xml
<!-- 锁定版本号 -->
<properties>
    <activemq.version>5.16.5</activemq.version>
    <antlr2.version>2.7.7</antlr2.version>
    <appengine-sdk.version>1.9.98</appengine-sdk.version>
    <artemis.version>2.19.1</artemis.version>
    <aspectj.version>1.9.7</aspectj.version>
    <!-- ....... -->
</properties>

<!-- 依赖管理 -->
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.apache.activemq</groupId>
            <artifactId>activemq-amqp</artifactId>
            <version>${activemq.version}</version>
        </dependency>
        <dependency>
            <groupId>org.apache.activemq</groupId>
            <artifactId>activemq-blueprint</artifactId>
            <version>${activemq.version}</version>
        </dependency>
    </dependencies>
    <!-- ....... -->
</dependencyManagement>
```

## 不继承parent

如果因为一些特殊原因无法直接继承parent时，可以手写 `dependencyManagement` ，限制 `import` 范围来实现相同的效果，而不需要从零开始引入各种插件。

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <!-- Import dependency management from Spring Boot -->
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>2.7.4</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

