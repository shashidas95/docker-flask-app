# Python Docker Web Application Documentation

This document provides step-by-step instructions to build a Docker image for a Python Flask web application, create a Docker volume, and run the container.

## Prerequisites

Ensure you have the following installed on your system:

- [Docker](https://www.docker.com/get-started)
- [Git](https://git-scm.com/)

## Step-by-Step Instructions

### 1. **Clone the repository**:

    ```sh
    git clone https://github.com/shashidas95/docker-flask-app.git
    cd docker-flask-app
    ```

### 2. Build the Docker Image

First, navigate to the project directory containing the `Dockerfile` and build the Docker image.

```sh
docker build -t my-flask-image .
```

This command creates a Docker image named `my-flask-image` using the instructions in the `Dockerfile`.

### 3. Create and Inspect a Docker Volume

Create a Docker volume to persist data outside the container.

```sh
docker volume create my_volume
```

You can inspect the volume to check its details.

```sh
docker volume inspect my_volume
```

### 4. List Docker Images

Check the list of Docker images to ensure your image was created successfully.

```sh
docker images
```

### 5. Run the Docker Container

Run a container from the created image, mapping ports and mounting the volume.

```sh
docker run -d -p 8080:8080 --name my-flask-container -v my_volume:/app my-flask-image
```

Explanation:

- `-d`: Run the container in detached mode.
- `-p 8080:8080`: Map port `8080` of the host to port `8080` of the container.
- `--name my-flask-container`: Assign a name to the running container.
- `-v my_volume:/app`: Mount the Docker volume `my_volume` to the `/app` directory in the container.
- `my-flask-image`: The name of the image to run.

### 6. Check Running Containers

Verify that your container is running.

```sh
docker ps
```

### 7. Access the Application

Open your web browser and navigate to `http://0.0.0.0:8080`. You should see the message "hello world".

### 8. Tag and Push the Docker Image

Tag the Docker image for pushing to a Docker registry.

```sh
docker tag my-flask-image shashidas/flask-image:1.0
```

Push the tagged image to Docker Hub or your Docker registry.

```sh
docker push shashidas/flask-image:1.0
```

## Summary of Docker Commands

- **Build Image**: `docker build -t my-flask-image .`
- **Create Volume**: `docker volume create my_volume`
- **Inspect Volume**: `docker volume inspect my_volume`
- **List Images**: `docker images`
- **Run Container**: `docker run -d -p 8080:8080 --name my-flask-container -v my_volume:/app my-flask-image`
- **List Running Containers**: `docker ps`
- **Tag Image**: `docker tag my-flask-image shashidas/flask-image:1.0`
- **Push Image**: `docker push shashidas/flask-image:1.0`

By following these steps, you can successfully build, run, and manage your Python Flask web application using Docker.
