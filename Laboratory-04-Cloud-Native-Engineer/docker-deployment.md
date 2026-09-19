# Docker Deployment – Nginx Containerized Web Server

*CCM101 – Laboratory 04 – Checkpoint 4 & 5 Technical Log*
*Environment: KillerCoda Ubuntu Playground with Docker pre-installed*

## Checkpoint 3 – Verify Docker Installation

```bash
docker --version
# Shows installed Docker client/server version. Used to confirm Docker is installed.

docker info
# Displays system-wide Docker status: server version, storage driver, CPUs, memory, running containers.

docker ps
# Lists running containers. Empty output on fresh playground means Docker daemon is running correctly.
```

**Evidence:** `screenshots/docker-version.png` – terminal showing `docker --version` and `docker info` output.

---

## Checkpoint 4 – Deploy Nginx Container

### 1. Pull Nginx image
```bash
docker pull nginx
```
Downloads the official Nginx image from Docker Hub to the local machine; does not run it yet.

![nginx pull](../screenshots/nginx-running.png)

### 2. Run Nginx container in detached mode with port mapping
```bash
docker run -d -p 8080:80 --name my-nginx nginx
```
Starts an Nginx container in the background (`-d`), maps host port 8080 to container port 80 (`-p 8080:80`), and names it `my-nginx` for easy management.

### 3. Verify web server is running
```bash
curl http://localhost:8080
```
Sends an HTTP request to the mapped port; receiving the `Welcome to nginx!` HTML confirms the containerized web server is live.

**Expected output snippet:**
```html
<title>Welcome to nginx!</title>
<h1>Welcome to nginx!</h1>
```

**Evidence:** `screenshots/nginx-running.png` – terminal showing `docker pull`, `docker run`, and `curl` output with Nginx HTML.

---

## Checkpoint 5 – Container Lifecycle Management

| # | Command | What it did (1 sentence) |
|---|---------|--------------------------|
| 1 | `docker ps` | Listed all currently running containers to confirm `my-nginx` was active and check its ID, image, ports, and uptime. |
| 2 | `docker stop my-nginx` | Gracefully stopped the running `my-nginx` container while keeping it on disk for restart or removal. |
| 3 | `docker ps` <br> `docker ps -a` | First command verified no containers are running, second showed `my-nginx` with `Exited` status to confirm it stopped. |
| 4 | `docker rm my-nginx` | Permanently deleted the stopped `my-nginx` container and its writable layer to free resources. |
| 5 (verify) | `docker ps -a` | Confirmed the container list is empty, proving the container was completely removed. |

Full lifecycle sequence to copy-paste:
```bash
docker ps
docker stop my-nginx
docker ps
docker ps -a
docker rm my-nginx
docker ps -a
```

**Evidence:** `screenshots/container-lifecycle.png` – terminal showing stop, ps, and rm execution.

> Note: If you get `No such container`, run `docker ps -a` to find the correct NAME or CONTAINER ID, then retry with that ID.
