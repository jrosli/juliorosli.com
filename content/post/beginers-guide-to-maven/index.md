---
date: "2018-09-11"
tags: ["maven"]
title: "Beginner's guide to Maven"
toc: true
---

## What is Maven?

{{% blockquote author="Wikipedia" %}}
Maven is a build automation tool used primarily for Java projects.
{{% /blockquote %}}

Maven has many use in Java projects, one of the use case that I use is for [dependency manager](https://medium.com/prodsters/what-are-dependency-managers-26d7d907deb8). If you know PHP and Laravel, most likely you will use [composer](https://getcomposer.org/doc/00-intro.md). In Node.js environment, [NPM](https://en.wikipedia.org/wiki/Npm_(software)). 


## Maven vs Gradle

In Java environment, the most popular build tool are **maven** and **gradle**. If you ever played with android environment, most likely you have used gradle before.

Every maven projects will have a file called [POM.xml](https://maven.apache.org/guides/introduction/introduction-to-the-pom.html). Every gradle projects will have file with extension **.gradle** – this file is written in groovy script.

I am not going to jump in the pros and the cons of maven vs gradle. But according to [survey in 2018 by Baeldung](https://www.baeldung.com/java-in-2018), 74% of Java projects use maven as it’s build tool. In my experience, when I search for online tutorials, usually there will be a POM.xml on the page. So it will be a good idea when we know one or two things about Maven

## Maven installation in 3 steps

Modern IDE like [Intellij Idea](https://www.jetbrains.com/idea/), usually maven is included, so we don’t need to install maven ourselves.

In case you need to install maven manually, you need java installed and configured. Below are the steps to install maven in Windows 7. 


### 1. Download Maven

Download maven from [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi) 

{{< figure
img="download-maven.png" 
caption="Downloading Maven" 
command="Resize" 
options="700x" >}}


### 2. Extract the file

{{< figure
img="extract-maven.png" 
caption="Extract the file, for example inside C:/" 
command="Resize" 
options="700x" >}}


### 3. Configure Environment Variable

To make it easier accessing maven, setup environment variable PATH to ```<maven_path>/bin```.

{{< figure
img="adding-environment-variable-1.png" 
caption="Open Edit the system environment variables" 
command="Resize" 
options="700x" >}}


{{< figure
img="adding-environment-variable-2.png" 
caption="Open Advanced > `Environment Variables`" 
command="Resize" 
options="700x" >}}

{{< figure
img="adding-environment-variable-3.png" 
caption="Edit the system environment variables" 
command="Resize" 
options="700x" >}}

While at at it, also check **JAVA_HOME** and **CLASSPATH** inside environment variables

{{< figure
img="java-home.png" 
caption="`JAVA_HOME`" 
command="Resize" 
options="700x" >}}

{{< figure
img="classpath.png" 
caption="`CLASSPATH` points to `<JDK>\lib\tools.jar`" 
command="Resize" 
options="700x" >}}


## Testing Maven installation
To test maven installation, execute:
{{<cmd>}}
mvn -v 
{{</cmd>}}

{{% note %}}
You might need to close and re-open cmd to have environment variables changes takes effect.
{{% /note %}}

{{< figure
img="testing-maven-installation.png" 
caption="`Congratulation! You have installed maven successfully." 
command="Resize" 
options="700x" >}}
