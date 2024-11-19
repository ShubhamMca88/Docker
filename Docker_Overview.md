
# Docker Overview

Docker is an open platform for developing, shipping, and running applications. It is a containerization platform that enables developers to package applications and their dependencies into a standardized unit called a container, which can run consistently across any environment.

## Docker Architecture Components

### Docker Daemon
- Listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes.
- Background service that plays a central role in managing Docker containers on a host machine.

### Docker Client
- The primary interface for interacting with Docker through commands like `docker run`.
- Communicates with the Docker daemon via Docker API.

### Docker Container
- A lightweight, standalone executable package that includes everything needed to run a piece of software.

### Docker Image
- A read-only template with instructions for creating a container.

### Docker Registries
- Stores Docker images. Public registries like Docker Hub or private registries can be used.

### Key Docker Objects
- **Images**
- **Containers**
- **Networks**
- **Volumes**

---

## Key Concepts

### Docker vs Virtual Machines
- Docker containers share the host OS kernel, making them lightweight and faster than VMs, which include a full OS with its kernel.

### Dockerfile
- A text file containing a series of commands to assemble a Docker image.

### Docker Compose
- Tool to define and manage multi-container Docker applications using a `docker-compose.yml` file.

### Docker Volume
- Used to save data created by containers, even if the container is stopped or deleted.

---

## Commands Overview

### Basic Commands
- `docker --version`: Show Docker version.
- `docker info`: Display system-wide information about Docker.
- `docker help`: List all commands or get help on a specific command.

### Image Management
- `docker images`: List all Docker images on the host.
- `docker pull <image>`: Download a Docker image from a registry.
- `docker build -t <name> <path>`: Build a Docker image from a Dockerfile.
- `docker rmi <image>`: Remove a Docker image.
- `docker tag <image_id or image_name> <new_name>`: Rename or re-tag an image.

### Container Management
- `docker ps`: List running containers.
- `docker ps -a`: List all containers (running and stopped).
- `docker run <image>`: Run a container from an image.
- `docker stop <container>`: Stop a running container.
- `docker start <container>`: Start a stopped container.
- `docker exec -it <container> <command>`: Run a command inside a running container.
- `docker logs <container>`: View logs from a container.

### Networking
- `docker network ls`: List all Docker networks.
- `docker network create <network_name>`: Create a custom network.
- `docker network connect <network> <container>`: Connect a container to a network.

### Volumes
- `docker volume ls`: List all Docker volumes.
- `docker volume create <volume_name>`: Create a volume.
- `docker run -v <volume>:/path/in/container <image>`: Mount a volume to a container path.

### Docker Compose Commands
- `docker-compose up`: Start and run services defined in `docker-compose.yml`.
- `docker-compose down`: Stop and remove containers, networks, and volumes created by `up`.
- `docker-compose build`: Build images defined in the `docker-compose.yml` file.

### Docker Swarm
- `docker swarm init`: Initialize a new swarm.
- `docker service create <options> <image>`: Create a new service in the swarm.
- `docker service scale <service>=<replicas>`: Adjust replicas for a service.

---

## Useful Flags and Options
- `-d`: Run a container in detached mode (background).
- `-it`: Run interactively with a terminal.
- `-p <host_port>:<container_port>`: Bind container ports to host ports.
- `--memory <limit>`: Limit memory usage for a container.
- `--cpus <limit>`: Limit CPU usage for a container.

---

## Cleaning and Pruning
- `docker container prune`: Remove all stopped containers.
- `docker system prune`: Remove unused objects like containers, networks, images, and volumes.

---

## File Management
- `.dockerignore`: Specifies files and directories to ignore during the build process.

---

## Starting and Stopping Docker Daemon
- `sudo systemctl start docker`: Start the Docker daemon.
- `sudo systemctl stop docker`: Stop the Docker daemon.
- `sudo systemctl restart docker`: Restart the Docker daemon.
