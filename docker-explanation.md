### What is Docker in Simple Terms?

Imagine you want to run a program on your computer, but that program has many dependencies (other software, libraries, or configurations). Instead of manually setting up everything, Docker packages the program, its dependencies, and the environment into something called a **container**. A container is a lightweight, portable environment that runs the program exactly the same way, no matter where it's running—whether it’s on your computer, a server, or in the cloud.

**Key idea:** Docker lets you "containerize" applications, so they run smoothly in any environment without worrying about setup or configuration conflicts.

### Basic Docker Concepts
- **Image**: A blueprint or template for a container. It’s like a recipe for what should be in the container.
- **Container**: A running instance of an image. It’s like the actual dish created from the recipe.
- **Dockerfile**: A file that contains the instructions to build a Docker image.
- **Docker Hub**: A repository (like GitHub for code) where Docker images can be stored and shared.
- **Azure Container Registry (ACR)**: A repository (like GitHub for code) where Docker images can be stored and shared but within the Azure ecosystem.

---

### Exercises to Practice Docker Basics

Here are some exercises to get you familiar with Docker commands like **push**, **pull**, **tag**, **build**, and **run**.

#### 1. **Docker Pull**
**Exercise**: Pull an existing image from Docker Hub.

```bash
docker pull hello-world
```
- **What happens**: This command fetches the `hello-world` image from Docker Hub.
- **Purpose**: Learn how to download (or "pull") an image from Docker Hub to your local machine.

#### 2. **Docker Run**
**Exercise**: Run the `hello-world` container.

```bash
docker run hello-world
```
- **What happens**: Docker will run the container, and you’ll see a simple message printed in the terminal.
- **Purpose**: Understand how to start (or "run") a container using a downloaded image.

#### 3. **Docker Build**
**Exercise**: Build your own Docker image using a simple `Dockerfile`.

1. Create a `Dockerfile` with the following content:
   ```Dockerfile
   # Use the official Node.js image from Docker Hub
   FROM node:14
   
   # Set the working directory inside the container
   WORKDIR /app

   # Copy the local files to the container's working directory
   COPY . .

   # Run a command inside the container to install dependencies
   RUN npm install

   # Command to run your application
   CMD ["node", "index.js"]
   ```
2. Create a basic `index.js` file:
   ```js
   console.log('Hello from Docker!');
   ```
   
3. Build the image:
   ```bash
   docker build -t my-node-app .
   ```
   - **What happens**: This command builds a new Docker image from the `Dockerfile` and tags it as `my-node-app`.
   - **Purpose**: Learn how to create your own Docker image using a Dockerfile.

#### 4. **Docker Tag**
**Exercise**: Tag your image with a different name or version.

```bash
docker tag my-node-app my-node-app:v1
```
- **What happens**: This tags your `my-node-app` image with the version `v1`.
- **Purpose**: Learn how to assign additional names or versions to your images.

#### 5. **Docker Push**
**Exercise**: Push your image to Docker Hub (you’ll need a Docker Hub account).

1. Log in to Docker Hub:
   ```bash
   docker login
   ```
2. Tag your image to match your Docker Hub repository:
   ```bash
   docker tag my-node-app:v1 your-dockerhub-username/my-node-app:v1
   ```
3. Push the image to Docker Hub:
   ```bash
   docker push your-dockerhub-username/my-node-app:v1
   ```
   - **What happens**: The image is uploaded to Docker Hub under your repository.
   - **Purpose**: Learn how to upload (or "push") your Docker images to a public or private repository.

#### 6. **Docker Pull & Run Custom Image**
**Exercise**: Pull the image you just pushed to Docker Hub and run it.

1. Pull the image from Docker Hub:
   ```bash
   docker pull your-dockerhub-username/my-node-app:v1
   ```
2. Run the container:
   ```bash
   docker run your-dockerhub-username/my-node-app:v1
   ```

- **What happens**: The container will run, and you'll see the output "Hello from Docker!" in the terminal.
- **Purpose**: Learn how to fetch and run your custom Docker images on any machine.

---

### Summary of Docker Commands:
- **`docker pull <image>`**: Download an image from Docker Hub.
- **`docker run <image>`**: Run a container from the image.
- **`docker build -t <name> <path>`**: Build a Docker image from a Dockerfile.
- **`docker tag <image> <new-name>`**: Assign a new name or version to an image.
- **`docker push <image>`**: Upload an image to Docker Hub.

### Command line list of Docker Commands:
- **`docker rm -f <imageid>`**: Remove an image.
- **`docker images`**: List all images available local.
- **`docker rm -vf $(docker ps -aq)`**: Remove all containers, also the ones running.
- **`docker rmi -f $(docker images -aq)`**: Remove all images.
