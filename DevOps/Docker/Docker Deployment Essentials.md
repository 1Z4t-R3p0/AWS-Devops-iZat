
>**These focus on deploying containers effectively in development, staging, and production environments.**

##  Image Tagging and Versioning

- Pulls and runs the **latest** version of the `redis` image.

```Dockerfile
docker run redis
```

- Pulls and runs a **specific version** (`4.0`) of the `redis` image.
  
```
docker run redis:4.0
```

---

##  Port Mapping

- Maps **port 80** inside the container to **port 8080** on the host.

```sh
docker run -p 8080:80 apache
```

- Access via: `http://localhost:8080`.

---

##  Volume Mapping and Persistent Data

- Maps host directory (`/opt/data_dir`) to container's MySQL data directory (`/var/lib/mysql`).

```sh
docker run -v /opt/data_dir:/var/lib/mysql mysql
```
### Benefits:

- **Persistent Storage**: Data survives container restarts/removals.
    
- **Data Portability**: Move `/opt/data_dir` to another machine/container.
    
- **Debugging**: Inspect DB files directly on the host.

---

##  Environment Variables

- Pass environment variables at runtime.

```sh
docker run -e VAR=value <image>
```

- Load multiple variables from a `.env` file.

```
docker run --env-file .env <image>
```

### `.env` example:

```
DB_USER=admin
DB_PASS=supersecure
```

---

## Auto-Restart Policies

```
docker run --restart always|unless-stopped|on-failure|no <image>
```

|Policy|Description|
|---|---|
|`no`|Never restart the container|
|`always`|Restart the container always|
|`on-failure`|Restart only if container exits with error|
|`unless-stopped`|Restart unless explicitly stopped by user|

- Ensures **high availability** and **resilience** in production environments.


---

##  Custom Networking

- Connect containers on the **same virtual network**.

```
docker network create mynet
```

- Enables **service discovery**:  
    - App can reach DB via `mysql:3306`.

```
docker run --network mynet --name mysql mysql docker run --network mynet --name app my-app
```


