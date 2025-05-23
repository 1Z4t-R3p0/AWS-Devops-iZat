# Introduction to Docker 

## What Are Containers?

- **Containers** are lightweight, standalone environments to run applications.
- They bundle **code + dependencies** together.
- Each container has its **own process, network, and storage mounts**.
- **Analogy**: Containers are like "virtual machines", but **faster and smaller**.
## What is Docker?

- **Docker** is a tool that makes it easy to create, deploy, and run containers.
- It automates container creation and management.

💬 *Think of Docker as a factory that builds and ships containers quickly!*

## Why Do We Need Docker?

- Consistent environment across development, testing, and production.
- **Isolation**: Apps don't affect each other.
- **Speed**: Faster startup compared to virtual machines.
- **Resource Efficiency**: Lightweight on system resources.

##  Key Concepts

 - **Image**          
	 - A blueprint/template to create a container. 

 - **Container**     
	 - A running instance of an image. 

 - **Docker Engine** 
	 - The runtime that manages containers. 
 
 - **Docker Hub**  
	 - A cloud repository for sharing images. 

---
#  Installing and Setup Docker

- Visit ➡️ [Docker Docs](http://docs.docker.com/)
- Download Docker for your platform (Windows / Mac / Linux).

### For Windows ;
- Download Link 
	- [Windows](https://desktop.docker.com/win/main/amd64/190950/Docker%20Desktop%20Installer.exe?_gl=1*1d3ubxo*_gcl_au*MTIyMTcxMDYyNC4xNzQ0NzA4NTU4*_ga*MTEyODg3MTc3LjE3NDA3NTA2OTU.*_ga_XJWPQMJYHQ*MTc0NTkwMzcwMy43LjEuMTc0NTkwNDQwNC42MC4wLjA.)

### For Mac ;
- Download Links 
	- [Docker Desktop for Mac with Apple silicon](https://desktop.docker.com/mac/main/arm64/Docker.dmg?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-mac-arm64&_gl=1*1kgq4x1*_gcl_au*MTIyMTcxMDYyNC4xNzQ0NzA4NTU4*_ga*MTEyODg3MTc3LjE3NDA3NTA2OTU.*_ga_XJWPQMJYHQ*MTc0NTkwMzcwMy43LjEuMTc0NTkwMzcxNi40Ny4wLjA.)
	- [Docker Desktop for Mac with Intel chip](https://desktop.docker.com/mac/main/amd64/Docker.dmg?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-mac-amd64)

### For Linux ;

> Downloading Methods
- Install using apt repo: 

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

```

```bash
# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

- ##### Installing the Docker packages:
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

- `.deb` download [link](https://desktop.docker.com/linux/main/amd64/190950/docker-desktop-amd64.deb?_gl=1*1mauz4z*_gcl_au*MTIyMTcxMDYyNC4xNzQ0NzA4NTU4*_ga*MTEyODg3MTc3LjE3NDA3NTA2OTU.*_ga_XJWPQMJYHQ*MTc0NTkwMzcwMy43LjEuMTc0NTkwNDQwNC42MC4wLjA.)

- #####  Installing the `.deb` file 
```sh
sudo apt-get update
sudo apt-get install ./docker-desktop-amd64.deb
```

- ##### Verify that the installation is successful by running the `hello-world` image:
```sh
sudo docker run hello-world
```

---
