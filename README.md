# Docker Command Cheat Sheet

This cheat sheet provides a quick reference for common Docker commands.

## Table of Contents

- [Getting Started](#getting-started)
- [Images](#images)
- [Containers](#containers)
- [Networking](#networking)
- [Volumes](#volumes)
- [Docker Compose](#docker-compose)
- [Docker Swarm](#docker-swarm)

## Getting Started

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker --version`                           | Display the installed Docker version                |
| `docker info`                                | Display system-wide information about Docker        |
| `docker help`                                | Display help for Docker commands                    |

---

## Images

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker pull <image>`                        | Pull an image from Docker Hub                       |
| `docker images`                              | List all available images                           |
| `docker rmi <image>`                         | Remove an image                                     |
| `docker build -t <image-name>:<tag> <path>`| Build an image from a Dockerfile                    |
| `docker tag <source-image> <target-image>`  | Tag an image with a new name                       |
| `docker search <term>`                       | Search for images on Docker Hub                     |

---

## Containers

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker run <image>`                         | Run a command in a new container                    |
| `docker run -d <image>`                      | Run a container in detached mode                    |
| `docker run -d  --name <name> -p <Serverport>:<containerport> <image>`                      | Run a container in detached mode give it specific name and map the port of the container                   |
| `docker run -tid --name <name> --memory 60mb -p 5050:80`                 | Run a container and specify memory for it    |
| `docker run -tid <image> sh`                 | Open shell of the container in current terminal     |
| `docker ps` or `docker container ls`         | List running containers                             |
| `docker ps -a` or `docker container ls -a`   | List all containers, including stopped ones         |
| `docker stop <container>`                    | Stop a running container                            |
| `docker stop -60 <container>`                | Stop a running container in 60 sec                  |
| `docker container kill <container>`          | Kill a running container                            |
| `docker start <container>`                   | Start a stopped container                           |
| `docker restart <container>`                 | Restart a container                                 |
| `docker rm <container>`                      | Remove a stopped container                          |
| `docker rm <container> --force`              | Remove a stopped container forcably                 |
| `docker exec -it <container> <command>`      | Execute a command inside a running container        |
| `docker logs <container>`                    | Fetch the logs of a container                       |

---

## Networking

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker network ls`                          | List all networks                                   |
| `docker network create <network-name>`      | Create a new network                                |
| `docker network rm <network-name>`          | Remove a network                                    |
| `docker network inspect <network-name>`     | Inspect a network                                   |
| `docker run --network <network-name> <image>`| Run a container in a specific network              |

---

## Volumes

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker volume ls`                           | List all volumes                                    |
| `docker volume create <volume-name>`        | Create a new volume                                 |
| `docker volume rm <volume-name>`            | Remove a volume                                     |
| `docker run -v <volume-name>:<container-path> <image>`| Mount a volume into a container             |

---

## Docker Compose

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker-compose up`                          | Start services defined in a `docker-compose.yml` file |
| `docker-compose down`                        | Stop and remove services defined in a `docker-compose.yml` file |
| `docker-compose ps`                          | List containers for the services defined in the `docker-compose.yml` file |
| `docker-compose logs`                        | View logs for services defined in the `docker-compose.yml` file |
| `docker-compose build`                       | Build or rebuild services defined in the `docker-compose.yml` file |

---

## Docker Swarm

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker swarm init`                          | Initialize a new Swarm                             |
| `docker swarm join --token <token> <manager-ip>:<port>` | Join a Swarm as a worker                 |
| `docker service create --name <service-name> <image>` | Create a new service in the Swarm          |
| `docker service ls`                          | List all services in the Swarm                    |
| `docker service scale <service-name>=<replica-count>` | Scale a service to the specified number of replicas |
| `docker node ls`                             | List all nodes in the Swarm                        |
