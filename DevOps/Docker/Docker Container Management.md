

>**These cover how to interact with, manage, and inspect running containers.**

## Running Containers with Commands

- Runs the `ubuntu` container and executes the command `sleep 5`.

```bash
docker run ubuntu sleep 5
```

- Executes a command (`cat /etc/hosts`) inside a **running** container.

```sh
docker exec <container_name> cat /etc/hosts
```

---

## Attach and Detach Modes

- Runs the container in **detached mode** (background process).

```sh
docker run -d <image>
```

>`-d`  ---> Detach Mode

- Attach your terminal to a **running container’s** standard output.

```sh
docker attach <container>
```

---

##  Interactive Terminal Mode

- Launches a container with an **interactive terminal (TTY)**.

```sh
docker run -it <image>
```

- `-i`: Keep STDIN open.
    
- `-t`: Allocate a pseudo-TTY.

---

## Inspecting and Viewing Logs

- Displays **detailed configuration and metadata** of a container (IP address, mounts, etc.)

```bash
docker inspect <container>
```

- Shows the container’s **stdout/stderr** output logs.
```sh
docker logs <container>
```

>Great for **debugging** issues.