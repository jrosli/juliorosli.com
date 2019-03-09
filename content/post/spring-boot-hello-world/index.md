---
date: "2018-09-02"
tags: ["spring","spring boot","maven"]
title: "Spring Boot - Hello World"
toc: true
---

### Tools used
    - Maven 3.5.2
    - Java 8
    - [start.spring.io](https://start.spring.io/)
    - Eclipse Java EE IDE for Web Developers

## Description
In this sample, we will create a spring boot application that will return **Hello World** when we go to the endpoint `/hello`.

## Generating POM.xml
Go to [start.spring.io](https://start.spring.io/)

{{< figure
img="Start-Spring-Io-Hello-World.png" 
caption="start.spring.io"
command="Original" >}}

1. The first part is project dependencies. We can specify components that we want to use in our project here. For example, if we want to create a web project, we can specify the project dependencies here, and click generate project.

2. The second part is project type, we can choose maven / gradle project, language used (for now, spring support `Kotlin`, `Groovy` and `Java`).

3. In the third part, we can specify the package name and project packaging (can be `war` or `jar`). If we choose war, we will need to deploy it on server (for example tomcat for web project). 

Download and extract the project. (My project named spring.zip)

{{< figure
img="Downloaded-Project.png" 
caption="Download and extract the project"
command="Original" >}}

### POM.xml
Since we are generating maven project, Inside the generated project, there will be a file named POM.xml. The spring initializr will configure the project dependencies inside POM.xml and prepare the project structures for us.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.training</groupId>
    <artifactId>spring</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>jar</packaging>
    <name>spring</name>
    <description>Demo project for Spring Boot</description>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
        <relativePath/>
    </parent>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

## Downloading Maven Dependencies
- Navigate to the folder and execute: 
{{<cmd>}}
mvn install
{{</cmd>}}


{{< figure
img="Downloading-Dependencies.png" 
caption="Downloading maven dependencies"
command="Original" >}}

{{< figure
img="Finished-Downloading-Dependencies.png" 
caption="Dependencies downloaded"
command="Original" >}}

Some IDE like eclipse or Intellij idea have functionality to automatically sync and download maven dependencies, but basically they are executing the command.

## Importing Project to Eclipse / other IDE
- Choose File > Import > Existing Maven Projects

{{< figure
img="import-maven-project-to-eclipse.png" 
caption="Importing Project to Eclipse"
command="Original" >}}

- Browse to the project folder and click finish.

{{< figure
img="import-maven-project-to-eclipse-2.png" 
caption="Choosing maven project to eclipse"
command="Original" >}}

### Basic Project Structure

{{< figure
img="Basic-structure-for-generated-spring-application.png" 
caption="Basic structure for generated spring application"
command="Original" >}}

- The main class is annotated with `@SpringBootApplication`.
- `@SpringBootApplication` is a shortcut for 3 annotations: `@Configuration`, `@EnableAutoConfiguration`, `@ComponentScan`
- The `@ComponentScan` annotation by default will scan all class (in the same package) annotated with `@ComponentScan`. [More info](http://www.javarticles.com/2016/01/spring-componentscan-annotation-example.html)
- In short, we will need to create the class function inside the the same package (or deeper) with the main class.

## Creating a RestController

- Create a new package and class

{{< figure
img="Project-structure-1.png" 
caption="Create new package and class"
command="Original" >}}

{{< code numbered="true" >}}
package com.training.spring.controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

[[[@RestController]]]
public class HelloController {

	[[[@RequestMapping("/hello")]]]
	public String Hello(){
		[[[return "Hello World!";]]]
	}
}
{{< /code >}}

1. First, we annotate the class to be a `@RestController`. This class will be a controller that will return a `ResponseBody`. If we trace back, it is coming from `@Controller`, and `@Controller` is a `@Component`. So this class will be initialized when the application starts.

2. Next, we map the endpoint with the function that will handle it. We will use `@RequestMapping(“/hello”)` which is a shortcut for `@RequestMapping(path=”/hello”)`. This means, when we access to the end point (`/hello`) it will execute this function. When we didn’t specify HTTPMethods for this annotation, it means we can use any HTTP method to access it. We can use (HTTP `GET`, `POST`, `PUT`, ….etc)

3. If we return String, it will return the string to the response body. But if we return an object, it will return json representation of the object. (automatically converted).

## Running the application
There are several ways to run the application:

### a. Running SpringBoot application using Eclipse
{{< figure
img="Run-using-eclipse.png" 
caption="Running SpringBoot application using Eclipse"
command="Original" >}}

### b. Running SpringBoot application using Maven
- To run the application, navigate to the project folder and execute:
{{<cmd>}}
mvn spring-boot:run
{{</cmd>}}

{{< figure
img="Run-using-maven.png" 
caption="Running SpringBoot application using Maven"
command="Original" >}}

## Test the application
- By default, spring application will open port 8080
- Open http://localhost:8080/hello

{{< figure
img="Testing-hello-world.png" 
caption="Hello World!"
command="Original" >}}

Other hello world sample: https://spring.io/guides/gs/rest-service/