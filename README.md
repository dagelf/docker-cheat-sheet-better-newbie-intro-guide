# A better docker guide for newbies and even kernel hackers.
And a cheat sheet!

IMO All the namings used in docker is wrong. Let me translate it for you, then it will instantly make sense! (If you think like me!)

Docker

image = Template!
*An image is a template for a machine, ideally running just one command. That means that a docker image contains a template filesystem as well as some metadata about what command it should run when it gets used. And image cannot be run! When you run it - it is called a container!*
 docker images -> list locally available images
 docker search -> find an image in an online registry (by default, the Docker hub)
 docker pull -> download an image from the registry
 docker push -> upload an image to the registry
 docker history -> shows the previous changes to an image
 docker import -> imports the filesystem for an image from standard input (your console!) as a tarball
 docker export -> outputs the filesystem of an image to standard output (to your console!) as a tarball
 
container = Instances of an image
 *When you run an "image" - it is not the image that is run, but rather, it creates a container, and then starts the container!*
 docker run <image> = returns a containerid -> creates a container from an image, on it's own clean filesystem as per the template, and then "starts" that container. 
 docker stop/kill -> stops a container
 docker ps -> shows running containers
 docker ps -a -> shows containers that have been created and ran in the past
 docker start -> start a container, running the last command that was run on it (or the CMD specified when creating it)
 docker inspect -> shows a lot of information about a container
 docker commit -> this is the opposite of run! It creates an image from a container
 docker rm -> remove a container (ie. one of the many you might still have listed under "docker ps -a"
 docker top -> shows the processes in your container
 docker exec -> runs a command in the container and shows its output
 docker cp -> copy files to/from the container
 
 volume = almost like a container, except it can only contain data, and you have to attach it to a container
  also a neat way to share data between containers
  
bind mount = a way to share a part of your host OS filesystem with containers

registry = an online hub that stores images
 docker login -> connect to a registry - by default, the Docker hub
 docker logout -> log out
 
TBC
 
