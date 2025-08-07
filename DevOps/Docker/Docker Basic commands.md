

#  Getting Started With Docker 
---
## Basic Docker Commands

 **Running a Container**
```bash
docker run hello-world
```

 **List Running Containers**
```bash
docker ps
```

**List All Containers (including stopped ones)**
```bash
docker ps -a
```
<img width="615" height="316" alt="Docker flowchart" src="https://github.com/user-attachments/assets/ea5396d9-7bc6-4e27-9881-99b8d81aa637" />

#### Dockerfile : 
 ```dockerfile
 # Use official Ubuntu as the base image
FROM ubuntu:22.04

# Install Apache2
RUN apt-get update && \
    apt-get install apache2 -y

# Copy your static HTML page (optional)
# Uncomment the line below if you have index.html in the same folder
# COPY index.html /var/www/html/

# Expose port 80
EXPOSE 80

# Start Apache in foreground
CMD ["apachectl", "-D", "FOREGROUND"]

```

Save this file as `Dockerfile` on your local machine (Windows, Linux, or Mac).

---
 **Docker Build Command**
```
docker build -t apache-ubuntu .
```

- `-t` is used to tag or name the image.

- `.` refers to the current directory where the Dockerfile is located.

---
 **View Docker Images**
```bash
docker images
```

 **Remove a Docker Image**
```dockerfile 
docker rmi <image_id>  ## Use -f for Force Remove 
```

**Stop a Running Container**
```bash
docker stop <container_id_or_name>
```

 **Remove a Container**
```bash
docker rm <container_id_or_name>
```

 **Download (Pull) an Image**
```bash
docker pull nginx
```

 **Pull and Run Together**
```bash
docker run nginx
```

