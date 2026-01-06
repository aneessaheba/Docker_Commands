# Docker: What It Is and How to Dockerize a Project

## What Is Docker?

Docker is an **open-source platform** for building, shipping, and running applications inside **containers**.

A container includes the application code, runtime (such as Python), system tools, libraries, dependencies, and configuration files.

Because everything is bundled together, Docker allows applications to run **consistently across different environments**, such as local machines, servers, or cloud platforms.

**Build once, run anywhere.**

## Why Use Docker?

Docker helps eliminate environment-related issues, ensures consistency across systems, it is lightweight compared to virtual machines, enables easy deployment and scalability, and is widely used in cloud, machine learning, and web applications.

## Steps to Dockerize a Project

### 1. Go to the project directory
```bash
cd my_project
```

### 2. Create a `requirements.txt` file to store dependencies
```bash
pip freeze > requirements.txt
```

### 3. Create a `Dockerfile`
Create a file named `Dockerfile` (no extension) and add the following content:
```dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

### 4. Build the Docker image
```bash
docker build -t my-python-app .
```

### 5. Check the Docker images created on your system
```bash
docker images
```

### 6. Run the Docker container

**For a normal Python application:**
```bash
docker run my-python-app
```

**For Streamlit or web applications:**
```bash
docker run -p 8501:8501 my-python-app
```

**Run container in detached mode (background):**
```bash
docker run -d -p 8501:8501 my-python-app
```

**Run container with a custom name:**
```bash
docker run --name my-app-container -p 8501:8501 my-python-app
```

### 7. Verify running Docker containers

**See all running containers:**
```bash
docker ps
```

**See all containers (including stopped ones):**
```bash
docker ps -a
```

### 8. View container logs
```bash
docker logs <container_id>
```

**Follow logs in real-time:**
```bash
docker logs -f <container_id>
```

### 9. Execute commands inside a running container
```bash
docker exec -it <container_id> /bin/bash
```

### 10. Stop a running container
```bash
docker stop <container_id>
```

### 11. Start a stopped container
```bash
docker start <container_id>
```

### 12. Restart a container
```bash
docker restart <container_id>
```

### 13. Remove a stopped container
```bash
docker rm <container_id>
```

**Force remove a running container:**
```bash
docker rm -f <container_id>
```

### 14. Remove the Docker image
```bash
docker rmi my-python-app
```

**Force remove an image:**
```bash
docker rmi -f my-python-app
```

### 15. Remove all stopped containers
```bash
docker container prune
```

### 16. Remove all unused images
```bash
docker image prune -a
```

### 17. View Docker disk usage
```bash
docker system df
```

### 18. Clean up everything (containers, images, networks, cache)
```bash
docker system prune -a
```

### 19. Tag an image for Docker Hub
```bash
docker tag my-python-app username/my-python-app:latest
```

### 20. Push image to Docker Hub
```bash
docker push username/my-python-app:latest
```

### 21. Pull an image from Docker Hub
```bash
docker pull username/my-python-app:latest
```

### 22. Create a `.dockerignore` file
Create a `.dockerignore` file to exclude unnecessary files from the build:
```
__pycache__
*.pyc
*.pyo
*.pyd
.env
.git
.gitignore
.vscode
.idea
*.md
venv/
env/
```

## Useful Docker Compose Commands

If using `docker-compose.yml`:
```bash
# Start services
docker-compose up

# Start services in detached mode
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs

# Rebuild images
docker-compose build
```

## Conclusion

Docker makes applications **portable, reproducible, and easy to deploy**.

