# Laboratory 04 – Cloud-Native Engineer

*Rogelio A. Mende – BSIT 4F – CCM101 Cloud Computing*
*Mission 4: The Cloud-Native Engineer – CloudNova Technologies*

## Mission Overview

As a newly promoted Cloud-Native Engineer at CloudNova Technologies, this mission addresses a client complaint that traditional Virtual Machines take too long to boot and waste RAM. The task was to research the shift from virtualization to containerization, then perform a live technical demonstration by deploying a containerized Nginx web server with Docker on KillerCoda in seconds, and document replicable commands for the client's IT team. A traditional sysadmin manages servers, but a cloud-native engineer manages the services running on them.

## Objectives

- Differentiate between traditional Virtual Machines (VMs) and Containers
- Access a Docker-enabled cloud environment using KillerCoda
- Execute fundamental Docker CLI commands
- Pull, run, manage, and terminate a containerized application (Nginx)
- Create professional technical documentation using Markdown
- Continue developing a well-organized GitHub Cloud Computing Portfolio

## Docker Commands Executed

All commands run in KillerCoda Ubuntu Playground:

**Checkpoint 3 – Verify installation:**
```bash
docker --version
docker info
docker ps
```

**Checkpoint 4 – Deploy Nginx:**
```bash
docker pull nginx
docker run -d -p 8080:80 --name my-nginx nginx
curl http://localhost:8080
```

**Checkpoint 5 – Lifecycle:**
```bash
docker ps
docker stop my-nginx
docker ps
docker ps -a
docker rm my-nginx
docker ps -a
```

See `docker-deployment.md` for full explanation and `screenshots/` for evidence:
- `screenshots/docker-version.png`
- `screenshots/nginx-running.png`
- `screenshots/container-lifecycle.png`

## Skills Learned

- Understanding container architecture (shared kernel, namespaces, cgroups) vs. hypervisor-based VMs
- Using Docker CLI to pull images from Docker Hub, run detached containers, and map ports
- Verifying deployments with `curl` and `docker ps`
- Managing container lifecycle (stop, remove, verify cleanup)
- Writing structured Markdown technical documentation with code blocks, tables, and screenshot links
- Organizing a GitHub portfolio with consistent folder structure and commits per checkpoint

## Challenges Encountered

- **KillerCoda session expiry:** Playgrounds are ephemeral (about 1 hour). Solution: complete commands quickly and take screenshots immediately.
- **Port already in use:** If port 8080 is busy, error `bind: address already in use`. Solution: use `-p 8081:80` or `docker ps` to find conflicts, then `docker stop/rm` old containers.
- **Image pull slowness:** First `docker pull nginx` can be slow on shared network. Solution: wait for completion, do not interrupt; verify with `docker images`.
- **Screenshot naming:** Must match exact names `docker-version.png`, `nginx-running.png`, `container-lifecycle.png`. Solution: rename before `git add`.
- **Forgetting container name:** `docker stop` fails if name is wrong. Solution: always run `docker ps -a` first to copy exact NAME/ID.

## Repository Structure

```
Laboratory-04-Cloud-Native-Engineer/
├── README.md
├── virtualization-vs-containers.md
├── docker-deployment.md
├── reflection.md
└── screenshots/
    ├── docker-version.png
    ├── nginx-running.png
    └── container-lifecycle.png
```
