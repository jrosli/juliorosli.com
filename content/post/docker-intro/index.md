---
date: "2018-08-23"
tags: ["docker"]
title: "Docker Intro"
toc: false
---

## What is Docker?

{{% blockquote author="Wikipedia" %}}
Docker is a computer program that performs operating-system-level virtualization, also known as “containerization”.
{{% /blockquote %}}

After playing with it a couple days ago, some of the important points are:

- Docker is one of application that enables “containerization”. Other containerization application: [Linux Containers](https://linuxcontainers.org/)
- Docker is primarily developed for Linux environment. It use resource relocation feature in Linux Kernel. [Wikipedia](https://en.wikipedia.org/wiki/Docker_(software)#Technology)
- To use docker in Windows, we need to run a Linux VM on Windows.
- On windows 7, we will need to use [Docker Toolbox](https://docs.docker.com/toolbox/overview/)
- The docker toolbox includes Oracle VirtualBox to run the VM.
- On newer windows machine like Windows 10, we do not need Oracle VirtualBox.

## Running Docker on Windows 7

- Download and install Docker Toolbox
- Run Docker Quickstart Terminal

{{< figure
img="Docker-Quickstart-Terminal.png" 
caption="Docker Quickstart Terminal" 
command="Original"  >}}

- From what I’ve observed, Docker Quickstart Terminal will search and turn on the VM on Oracle Virtual Box
- If the VM is not exists, it will search for `boot2docker.iso` inside `%userprofile%.docker\machine\cache` 

{{< figure
img="Running-Docker-Quickstart-Terminal.png" 
caption="If everything runs smoothly, we will see the docker’s whale, Moby Dock" 
command="Original"  >}}

Use [Kinematic](https://kitematic.com/) if you want to use GUI to control Docker

## Docker Hello World

To test if the docker configured properly, lets start with a Docker’s Hello World.
Execute below command in terminal:
{{<cmd>}}
docker run hello-world
{{</cmd>}}

{{< figure
img="Docker-Hello-World.png" 
caption="Congratulation! Docker installed successfully!" 
command="Original"  >}}

In simple terms, when the command executed:

1. Docker client ask docker daemon to search for `docker image` with name `hello-world` in local repository or public repository of docker image.
2. Docker daemon create a new container from `docker image` that found
3. Docker execute `command` that specified on the `docker image`, which is to print the message

## DockerFile, DockerImage, Container Relationship

{{< figure
img="DockerFile-DockerImage-Container.png" 
caption="Dockerfile, Docker Image, Container relationship" 
command="Original"  >}}

1. Everything starts with the `Dockerfile`. The `Dockerfile` is the source code of the Image.

2. Once the `Dockerfile` is created, we build it to create the `image` of the container (`DockerImage`). The `image` is just the “compiled version” of the “source code” which is the `Dockerfile`.

3. Next, we can use the image to run containers. A running container is very similar, in many aspects, to a virtual machine ([but it is not a virtual machine](https://www.backblaze.com/blog/vm-vs-containers/)).

Good resource to start:

https://www.youtube.com/watch?v=YFl2mCHdv24

https://docker-curriculum.com/

https://stackoverflow.com/questions/23735149/what-is-the-difference-between-a-docker-image-and-a-container 