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
| `docker-compose up`                          | Start all services defined in a `docker-compose.yml` file. Creates and starts containers as needed. |
| `docker-compose up -d`                       | Start services in detached mode (running in the background). |
| `docker-compose down`                        | Stop and remove containers, networks, volumes, and images created by `docker-compose up`. |
| `docker-compose down -v`                     | Stop and remove services along with their associated volumes. |
| `docker-compose ps`                          | List the status of containers for the services defined in the `docker-compose.yml` file. |
| `docker-compose logs`                        | View logs for all running services. By default, it displays real-time logs. |
| `docker-compose logs -f`                     | Follow logs in real-time for services defined in the `docker-compose.yml` file. |
| `docker-compose build`                       | Build or rebuild images for services defined in the `docker-compose.yml` file. |
| `docker-compose build --no-cache`            | Build services without using the cache. Forces a fresh build. |
| `docker-compose pull`                        | Pull the latest images for all services defined in the `docker-compose.yml` file. |
| `docker-compose start`                       | Start containers for services that were stopped but not removed. |
| `docker-compose stop`                        | Stop running containers without removing them. They can be restarted later using `docker-compose start`. |
| `docker-compose restart`                     | Restart running containers for services defined in the `docker-compose.yml` file. |
| `docker-compose exec <service-name> <command>` | Execute a command inside a running service container. |
| `docker-compose run <service-name> <command>` | Run a one-off command in a new container for a service. |
| `docker-compose config`                      | Validate and view the configuration of the `docker-compose.yml` file. |
| `docker-compose config --services`           | List all services defined in the `docker-compose.yml` file. |
| `docker-compose config --volumes`            | List all volumes defined in the `docker-compose.yml` file. |
| `docker-compose kill`                        | Forcefully stop running containers for all services. |
| `docker-compose rm`                          | Remove stopped service containers. Prompts for confirmation by default. |
| `docker-compose rm -f`                       | Remove stopped service containers without confirmation. |
| `docker-compose version`                     | Display the installed version of Docker Compose. |

---

## Docker Swarm

| Command                                      | Description                                         |
|----------------------------------------------|-----------------------------------------------------|
| `docker swarm init`                          | Initialize a new Swarm and make the current node the Swarm manager. |
| `docker swarm join --token <token> <manager-ip>:<port>` | Join a Swarm as a worker node using the provided token and manager IP. |
| `docker swarm join-token manager`           | Display the join token command to add another manager node. |
| `docker swarm join-token worker`            | Display the join token command to add a worker node. |
| `docker swarm leave`                        | Leave the Swarm. Use `--force` if the node is a manager. |
| `docker service create --name <service-name> <image>` | Create a new service in the Swarm using the specified image. |
| `docker service update <service-name> --image <new-image>` | Update an existing service to use a new image. |
| `docker service ls`                          | List all services running in the Swarm. |
| `docker service ps <service-name>`           | List all tasks (containers) of a specific service. |
| `docker service logs <service-name>`         | View logs for a specific service. |
| `docker service rm <service-name>`           | Remove a service from the Swarm. |
| `docker service scale <service-name>=<replica-count>` | Scale a service to the specified number of replicas. |
| `docker node ls`                             | List all nodes in the Swarm, showing their roles, availability, and status. |
| `docker node ps <node-id>`                   | List tasks running on a specific node. |
| `docker node rm <node-id>`                   | Remove a node from the Swarm. The node must leave the Swarm first. |
| `docker node update --availability <active|pause|drain> <node-id>` | Change the availability state of a node. |
| `docker stack deploy -c <compose-file.yml> <stack-name>` | Deploy a stack using a Docker Compose file. |
| `docker stack ls`                            | List all deployed stacks in the Swarm. |
| `docker stack ps <stack-name>`               | List all tasks in a stack. |
| `docker stack rm <stack-name>`               | Remove a deployed stack. |
| `docker inspect <object>`                    | Inspect the details of any Docker object (node, service, task, etc.). |
| `docker events`                              | Display real-time events from the Swarm. |
| `docker swarm update --task-history-limit <value>` | Update Swarm settings, such as task history limit. |
