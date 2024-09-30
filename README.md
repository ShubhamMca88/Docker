
# Docker Notes

## 1. Introduction to Docker
Docker is an open-source platform designed to automate the deployment, scaling, and running of applications using containerization.

- **Containerization**: Process of packaging an application along with its dependencies into a container to ensure consistency across different environments.

### Key Concepts
- **Images**: Immutable, lightweight, and standalone executable packages that include everything needed to run a piece of software (code, runtime, libraries, environment variables, etc.).
- **Containers**: Running instances of Docker images.
- **Dockerfile**: A text file containing instructions for building a Docker image.
- **Docker Hub**: A cloud-based registry where Docker users can create, test, and store Docker images.

---

## 2. Installing Docker
- Install Docker from the [official Docker website](https://www.docker.com/get-started).
- Verify installation:
    ```bash
    docker --version
    ```

---

## 3. Docker CLI Commands

### 3.1 Working with Images
- **Pull an image** from Docker Hub:
    ```bash
    docker pull <image_name>
    ```
- **List all images**:
    ```bash
    docker images
    ```
- **Remove an image**:
    ```bash
    docker rmi <image_id>
    ```

### 3.2 Working with Containers
- **Run a container**:
    ```bash
    docker run <image_name>
    ```
- **List running containers**:
    ```bash
    docker ps
    ```
- **Stop a container**:
    ```bash
    docker stop <container_id>
    ```
- **Remove a container**:
    ```bash
    docker rm <container_id>
    ```

### 3.3 Running a Container in Detached Mode
- **Detached mode** allows a container to run in the background:
    ```bash
    docker run -d <image_name>
    ```

### 3.4 Accessing a Running Container
- **Open a terminal session** inside a running container:
    ```bash
    docker exec -it <container_id> /bin/bash
    ```

---

## 4. Dockerfile

### 4.1 Creating a Dockerfile
- A `Dockerfile` defines the environment for the application and how the container should behave.
- Example `Dockerfile`:
    ```Dockerfile
    # Base image
    FROM python:3.8

    # Set the working directory
    WORKDIR /app

    # Copy local files to container
    COPY . /app

    # Install dependencies
    RUN pip install -r requirements.txt

    # Define the command to run the app
    CMD ["python", "app.py"]
    ```

### 4.2 Building an Image from a Dockerfile
- Build the image using the `Dockerfile`:
    ```bash
    docker build -t <image_name> .
    ```

---

## 5. Docker Compose
Docker Compose is a tool for defining and running multi-container Docker applications.

### 5.1 Example `docker-compose.yml`
```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    build: .
    volumes:
      - .:/app
    command: python app.py
```

### 5.2 Docker Compose Commands
- **Start services**:
    ```bash
    docker-compose up
    ```
- **Stop services**:
    ```bash
    docker-compose down
    ```

---

## 6. Docker Volumes
Docker volumes are used to persist data generated by containers.

- **Create a volume**:
    ```bash
    docker volume create <volume_name>
    ```
- **Mount a volume**:
    ```bash
    docker run -v <volume_name>:/path/in/container <image_name>
    ```

---

## 7. Docker Networking
Docker provides various networking options for communication between containers.

### 7.1 Listing Networks
```bash
docker network ls
```

### 7.2 Creating a Network
```bash
docker network create <network_name>
```

### 7.3 Connecting a Container to a Network
```bash
docker network connect <network_name> <container_name>
```

---

## 8. Common Docker Use Cases
- **Microservices**: Use Docker to package and run microservices independently.
- **Continuous Integration (CI)**: Docker is used in CI pipelines to ensure consistency in builds and testing environments.
- **Scaling Applications**: Docker containers can be scaled easily by increasing the number of container instances.

---

## 9. Docker Best Practices
- **Minimize Image Size**: Use small base images (like `alpine`).
- **Use Multi-stage Builds**: To reduce image size and build time.
- **Avoid Storing Sensitive Information**: Don't store sensitive data (e.g., passwords) in Dockerfiles.

---

## 10. Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
