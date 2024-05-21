
# Docker 

Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

### Docker Image
A Docker image, or container image, is a standalone, executable file used to create a container. This container image contains all the libraries, dependencies, and files that the container needs to run. A Docker image is shareable and portable, so you can deploy the same image in multiple locations at once—much like a software binary file. 

You can store images in registries to keep track of complex software architectures, projects, business segments, and user group access. For instance, the public Docker Hub registry contains images such as operating systems, programming language frameworks, databases, and code editors. 

Images are made up from several layers, like.

run commands

Dependencies

Source Code
    
Parent Image


### Docker Container

It is a running instance of Docker Image. A Docker container is a runtime environment with all the necessary components—like code, dependencies, and libraries—needed to run the application code without using host machine dependencies. This container runtime runs on the engine on a server, machine, or cloud instance. The engine runs multiple containers depending on the underlying resources available. 


## Basic Commands

#### build docker image from dockerfile
``` 
docker build -t myapp .
```
where,  **-t** means tag which we want to gave our image. **myapp** name of our image and **.** means relative path to our dockerfile. (in this case when we run command on terminal our dockerfile was in same folder)


#### get all images
``` 
docker images
```

#### show only running containers
```
docker ps
```


#### show all containers 
```
docker ps -a
```


#### create$run container from image 
```
docker run --name myapp_c2 -p 4000:4000 -d  myapp

```

where **--name** this flag used to specify name of container (in this case myapp_c2), **-p** used to expose port 4000:4000, Here port no on right side is port exposed by container and on left port we wanna map to the container on our computer and **-d** means deteched mode.(it means when run container kill terminal not hang)


#### stop running container
```
docker stop name_of_container
```


#### start already created container (if stop)
```
docker start name_of_container
```