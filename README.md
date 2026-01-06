# Docker Explained: What It Is and How to Dockerize a Project 

## What Is Docker?

Docker is an **open-source platform** for building, shipping, and running applications inside **containers**.

A container includes the application code, runtime (such as Python), system tools, libraries, dependencies, and configuration files.  
Because everything is bundled together, Docker allows applications to run **consistently across different environments**, such as local machines, servers, or cloud platforms.

**Build once, run anywhere.**

## Why Use Docker?

Docker helps eliminate environment related issues, ensures consistency across systems,it is lightweight compared to virtual machines, enables easy deployment and scalability, and is widely used in cloud, machine learning, and web applications.

## Steps to Dockerize a Project

1. Go to the project directory:
   `cd my_project`

2. Create a `requirements.txt` file to store dependencies:
   `pip freeze > requirements.txt`

3. Create a file named `Dockerfile` (no extension) and add the following content:
   ```example Dockerfile
   FROM python:3.10-slim
   WORKDIR /app
   COPY requirements.txt .
   RUN pip install --no-cache-dir -r requirements.txt
   COPY . .
   CMD ["python", "app.py"]

5. Check the Docker images created on your system:
   `docker images`

6. Run the Docker container:
   - For a normal Python application:
     `docker run my-python-app`
   - For Streamlit or web applications:
     `docker run -p 8501:8501 my-python-app`

7. Verify running Docker containers:
   `docker ps`

8. Stop a running container:
   `docker stop <container_id>`

9. Remove a stopped container:
   `docker rm <container_id>`

10. Remove the Docker image:
    `docker rmi my-python-app`

## Conclusion

Docker makes applications **portable, reproducible, and easy to deploy**.  


