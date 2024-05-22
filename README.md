
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

### build docker image from dockerfile
``` 
docker build -t myapp .
```
where,  **-t** means tag which we want to gave our image. **myapp** name of our image and **.** means relative path to our dockerfile. (in this case when we run command on terminal our dockerfile was in same folder)


### get all images
``` 
docker images
```

### show only running containers
```
docker ps
```


### show all containers 
```
docker ps -a
```


### create$run container from image 
```
docker run --name myapp_c2(container-name) -p 4000:4000 -d  myapp(image-name)

```

where **--name** this flag used to specify name of container (in this case myapp_c2), **-p** used to expose port 4000:4000, Here port no on right side is port exposed by container and on left port we wanna map to the container on our computer and **-d** means deteched mode.(it means when run container kill terminal not hang)


### stop running container
```
docker stop name_of_container
```


### start already created container (if stop)
```
docker start name_of_container
```



### command to remove image
```
docker image rm name_of_image
```


### command to remove image (if image is used by container)
```
docker image rm name_of_image -f
```


### command to remove container
```
docker container rm name_of_container
```

`
 Another way to delete image is, if we want to delete image that is used by any container it will throw error, so for this first delete container that is using image and you can delete image by using simple command
`


### Delete all images and container
```
docker system prune -a
```





### create&run container from image 
```
docker run --name myapp_c2(container-name) -p 4000:4000 -d --rm myapp(image-name)

```
Here **--rm** means, When we stop this container it will automatically delete container.


### Docker Volume
The purpose of using Docker volumes is to persist data outside the container so it can be backed up or shared.

you create an image and run container from that image. Suppose you made changes in localfile and it does not reflect on container. volume is also used here any change made in localfile reflect on container



**Below is command**,

```
docker run --name myapp_c_nodemon -p 4000:4000 --rm
 -v /home/work/Documents/docker-practice:/app -v /app/node_modules myapp:nodemon
```

Here this **-v /home/work/Documents/docker-practice/api:/app** it is volumn it will map our project to container folder.

local project location     --->  /home/work/Documents/docker-practice/api
    
container project location ---> /app

And below is 2nd volume also called anonymous volume

**-v /app/node_modules**

we create 2nd volume because every change made in local reflect to container. what if someone delete node_modules from local it will delete from container it will cause issues becaues our container need node_modules for manage dependencies.

so in above command when first volume execute it will map whole project to container folder the second volume map node_modules from container folder to someone places on our computer managed by docker. (means no worry about this).

`using volume every change made in local will keep sync with container folder`