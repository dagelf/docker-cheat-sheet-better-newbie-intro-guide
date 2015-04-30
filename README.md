## A better docker guide for newbies and even kernel hackers.
###And a cheat sheet!

IMO All the namings used in docker is wrong. Let me translate it for you, then it will instantly make sense! (If you think like me!)

##Docker

###image = Template!

*An image is a template for a machine that ideally runs just one command. That means that a docker image contains a template filesystem containing all the files and commands needed as well as some metadata about what command or startup script it should run when it gets used. An image cannot be run! When you run it - it is called a container! (The images is in turn created by a dockerfile, which is the recipe for creating it.)*

 **docker images** -> list locally available images
 
 **docker search** -> find an image in an online registry (by default, the Docker hub)

 **docker pull** -> download an image from the registry

 **docker push** -> upload an image to the registry

 **docker history** -> shows the previous changes to an image

 **docker import** -> imports the filesystem for an image from standard input (your console!) as a tarball

 **docker export** -> outputs the filesystem of an image to standard output (to your console!) as a tarball
 
###container = Instances of an image
 *When you run an "image" - it is not the image that is run, but rather, it creates a container, and then starts the container!*

 **docker run <image>** = returns a containerid -> creates a container from an image, on its own clean filesystem as per the template, and then "starts" that container. 

 **docker stop** or **docker kill** -> stops a container. Everything is still there, it's just not running anymore. 

 **docker ps** -> shows running containers

 **docker ps -a** -> shows containers that have been created and ran in the past

 **docker start** -> start a container, running the last command that was run on it (or the CMD specified when creating it)

 **docker inspect** -> shows a lot of information about a container

 **docker commit** -> this is the opposite of run! It creates an image from a container

 **docker rm** -> remove a container (ie. one of the many you might still have listed under "docker ps -a"

 **docker top** -> shows the processes in your container

 **docker exec** -> runs a command in the container and shows its output

 **docker cp** -> copy files to/from the container
 
###volume
Almost like a container, except it can only contain data, and you have to attach it to a container. Also a neat way to share data between containers.
  
###bind mount
A way to share a part of your host OS filesystem with containers.

###registry = an online hub that stores images
 **docker login** -> connect to a registry - by default, the Docker hub; Now you can push images

 **docker logout** -> log out from a registry; now you can't push images anymore

###Dockerfiles
A Dockerfile is a recipe for creating an image. So it's the list of commands you need to run to set up a template environment, on which you can run things.

##Naming
### Images
Images are named USERNAME/IMAGE:TAG

So, if your username is @Dagelf, and you have a CentOS image with a webserver installed, you can create or commit your image as **dagelf/centos:httpd**. Or maybe **dagelf/centos7:httpd**. Or perhaps **dagelf/centos:7** but I'm not sure where you'll put the httpd or "webserver" description... I'm still figuring this out. Unless you use the official CentOS images supplied, and build out from there: **centos/centos:7** which forms the base for your **dagelf/centos:httpd**

## Updating images
So docker Hub has a really cool service where they will automatically build images based on Dockerfiles - so whenever you pull an image from them, it will always be up to date. But the question is, how do you keep your image updated, once you've pulled it and started using it? Well, the simple answer is: you don't. You set up your application flow so that when you want to update, you simply pull it again, and start a new container. When the new container is running smoothly, you simply stop the old container. Of course you can just keep on updating your old containers with the usual update commands, but the philosophy - and beauty - of docker, is that you can start from scratch, every time, with just one command. If you want to. Why? Because it forces you to document your setup process in a repeatable (and hence portable) manner - which in turn makes a lot of other things easier...

##TBC
 Feel free to update/edit/format. Thanks!
