# Containers solutions 

Software can be deployed in virtual operating systems called containers, which are isolated bundles with their own software, libraries, and configuration files. These containers can communicate across each other and cen be easily deployed with controlled environments, removing many issues that occur when unknown variables and software on servers interact and clash with other software. Due to the controlled and easily replicable nature of containers, they come in handy when setting up applications across many, different platforms with varying degrees of resources and operating systems, software, and hardware, because as long as the platform can run Docker or similar container-based platforms, the containers are simple to set up.

## Docker

- [Docker documentation](https://docs.docker.com)
- [Docker downloads](https://docs.docker.com/get-docker/)

Docker is the prime example for containerized solutions, probably the best and widest known software with the most support.
Running Docker in Windows may require you to configure your HyperV.

#### Setup on Windows

## Docker compose

Docker Compose is a tool for Docker for managing multiple containers with YAML files. These containers can also be manged with CLI commands.

#### CLI

- [Official Documentation](https://docs.docker.com/compose/reference/)

- Build Docker Compose file (when stand in directory of a docker-compose.yml file)
  - $ `docker build`
- Run Docker Compose file (when stand in directory of a docker-compose.yml file)
  - $ `docker up`
- Remove all images
  - $ `docker down --rmi all`
- List containers
  - $ `docker ps`
- Kill/destroy a container
  - $ `docker kill [container id]`
- Start a container
  - $ `docker start [container id]`
- Stop a container
  - $ `docker stop [container id]`
- Remove a container
  - $ `docker rm`
- Remove alls topped containers
  - $ `docker ps -a -q -f status=exited xargs docker rm`

## Kubernetes

- [Kubernetes documentation](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)

TODO learn Kubernetes?