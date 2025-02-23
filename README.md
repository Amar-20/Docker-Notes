# Docker-Notes

## What is Docker?

Docker is a free open-source platform that helps developers build, manage, and run their applications in containers.

## Why do we need docker?

- Easy to install and run software without worrying about setup and dependencies.
- Can run software in isolation without worrying about other software running on the same machine simultaneously.
- Developers use docker containers to package their code, libraries, and dependencies.
- These containers are portable and independent of each other and can run in any environment.
- These qualities help the developers to run, test, and deploy their applications very quickly.

## Docker Basics:

When we run any software in docker it downloads the required “software image”(the single file which contains dependencies, libraries, and config files to run the program) then it runs the software image in containers.

Docker —> Software Image —> container(s).[can be multiple with the same software versions or different software.]

## Docker Ecosystem:

The Docker ecosystem consists of 6 different components.

- Docker image
- Docker Client
- Docker Server
- Docker Hub
- Docker compose
- Docker Machine

## Docker Image:

Docker image is a single file that contains the instructions for building a docker container. It's a snapshot of what will be there in the docker container. It contains code, config files, dependencies, and runtime dependencies and tools.

- This docker image contains two components.
1. File System Snapshot. (This contains all the depend., config etc.,, which should be there to run a particular application.)
2. Startup command. (This is the command that helps run the File system snapshot in a docker container.)

## Docker Container:

The Docker container is a package that contains all the necessary components needed to run an application. 

- It basically contains all the namespacing/segmentation of all the hardware, RAM, CPU, and network to run a process.
- And it also contains depends. , config files, etc., from “File System Snapshot.”

## Docker Server:

Docker server is nothing but a compute instance (VM, Personal Computer etc.) which is responsible for running the docker daemon process which in turn manages all the services provided by docker.

In docker a “Docker daemon”, also known as "dockerd", is **a background process that runs on a host machine and manages all aspects of Docker containers, including building, running, and distributing them**; essentially acting as the core component responsible for creating and managing Docker images, containers, networks, and storage volumes by listening for API requests from the Docker client and executing them

![alt text](<Screenshot 2025-02-23 150102.png>)

## Docker Client(CLI):

To communicate with the docker daemon(docker component) to execute a certain task like running a container, build some images that are all done via the docker client. Now, you’d have probably guessed it, The Docker CLI. Along with Docker CLI, Docker daemon also exposes a REST API which can be used to programmatically access services exposed by the daemon.

  
![alt text](<Screenshot 2025-02-23 151423.png>)

## Basics Docker Commands:

- Docker run —> used for creating and running a container from an image. 
Docker run<Image Name>
- Another type of run command
Docker run <Image name><command>
- “Docker run = Creating container (docker create <image name>) + starting container (docker start  -a<container ID>)” [to look at what happening in the container we use -a]
- To look at the list of running containers we use 
Docker ps
- To look for previously used containers we use
docker ps —all
- We can start the container again using
docker start -a <container ID> but, can’t change the container by giving a new command.
- Docker logs to look at how many times a container ran, and also helps in debugging.
docker logs <container ID>
- To stop a running container we have two options
1. Docker stop <container id> (takes time to stop the container )(sends SIGTERM)
2. Docker kill <container id> (kills the container immediately) ()
- To give additional commands to the running container we use 
docker exec -it <container id> <command>
Example: docker run redis
                 docker exec -it <container id><redis-cli> (but this process is repetitive if we have many commands to execute so we need to access the “container shell”.)
- To delete a container we use 
docker rm <container id>
- To delete an image we use
docker rmi <image id>

## Creating our docker image and running it.

So to create our image we need a docker file. 

In this docker file, we need to give three things to create docker image.

1. from <base image>
2. run <install req>
3. CMD [’ input command’]

![alt text](<Screenshot 2025-02-23 164159.png>)

![alt text](<Screenshot 2025-02-23 164224.png>)

Then use “docker build <docker file location>”

### Tagging the docker image ids:

![alt text](<Screenshot 2025-02-23 165431.png>)

To do this docker image naming we use a command


docker build -t amar/postgresql: latest
