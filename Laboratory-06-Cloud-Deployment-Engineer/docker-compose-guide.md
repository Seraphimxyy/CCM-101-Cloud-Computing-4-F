# Docker Compose Guide – Nextcloud + MariaDB Stack

*Rogelio A. Mende (Seraphimxyy) – BSIT 4F – CCM-101 Mission 6*

This guide documents the `docker-compose.yml` used in Checkpoint 3 so another engineer can understand and reproduce the deployment.

## Full Compose File

```yaml
version: '3'
services:
  database:
    image: mariadb:10.6
    environment:
      - MYSQL_ROOT_PASSWORD=cloudnova_root
      - MYSQL_PASSWORD=cloudnova_pass
      - MYSQL_DATABASE=nextcloud_db
      - MYSQL_USER=nextcloud_user
  app:
    image: nextcloud
    ports:
      - 8080:80
    environment:
      - MYSQL_PASSWORD=cloudnova_pass
      - MYSQL_DATABASE=nextcloud_db
      - MYSQL_USER=nextcloud_user
      - MYSQL_HOST=database
```

Created with:

```bash
mkdir nextcloud-deployment
cd nextcloud-deployment
nano docker-compose.yml
# paste exactly, spaces only, no Tabs – YAML is space-sensitive
# Ctrl+O, Enter to save – Ctrl+X to exit
```

Deployed and verified with:

```bash
docker-compose up -d
docker-compose ps
# open port 8080 via KillerCoda Traffic/Ports to see Nextcloud setup
docker-compose down
```

## 1. What does the `services:` block do?

The `services:` block is the blueprint that declares every container in the stack as Infrastructure as Code. Each key under it (`database:`, `app:`) defines one service: which `image:` to pull, which `ports:` to publish, and which `environment:` variables to inject.

When we run `docker-compose up -d`, Compose reads this block and:

1. Creates a private bridge network for the project.
2. Pulls `mariadb:10.6` and `nextcloud` if not present.
3. Starts both containers in the background (`-d` = detached) and links them to that network.
4. `docker-compose ps` then shows both services as `Up`, and `docker-compose down` stops and removes them together, so the whole two-tier system is managed as one unit instead of two manual `docker run` commands.

## 2. How did the Nextcloud app container know how to find the database container?

Through the environment variable `MYSQL_HOST=database`.

Docker Compose provides automatic internal DNS: each service name becomes a hostname on the shared project network. So `database` resolves to the MariaDB container's internal IP without us hard-coding anything.

The `app` service passes:

- `MYSQL_HOST=database` → where to connect
- `MYSQL_DATABASE=nextcloud_db`, `MYSQL_USER=nextcloud_user`, `MYSQL_PASSWORD=cloudnova_pass` → what credentials/database to use

These must match the values set in the `database` service (`MYSQL_DATABASE`, `MYSQL_USER`, `MYSQL_PASSWORD`). If they mismatch, Nextcloud cannot authenticate. This is why using the same Compose file for both sides guarantees they agree — a common source of error when typing two separate `docker run` commands.

No `ports:` is published for `database` because browsers never need direct access; only the `app` container needs to reach it internally.

## 3. What is the difference between `docker run` (Mission 4/5) and `docker-compose up -d`?

| `docker run` (imperative) | `docker-compose up -d` (declarative IaC) |
|---|---|
| Starts **one** container per command | Starts **entire multi-container stack** from one file |
| Flags must be retyped every time (`-d -p 8080:80 -e ... --name ...`) – prone to typos | Configuration is **saved, versioned, and reviewable** in `docker-compose.yml` |
| Linking two containers requires manual `--link` or network commands and correct order | Compose **creates the network, DNS, and startup order** automatically |
| Teardown is per-container (`docker stop`, `docker rm`) | Teardown is one command (`docker-compose down`) for containers + network |
| Hard to share exact deployment with teammate | Teammate runs same two commands (`up -d`, `ps`) and gets identical environment |

In short: `docker run` is typing instructions; `docker-compose up -d` is running code that *is* the infrastructure. That is the core IaC principle — repeatable, auditable, and pushable to GitHub.

## YAML Pitfalls to Avoid

- Use **spaces only, never Tabs**. A Tab causes `yaml: line X: found character '\t' that cannot start any token` and Compose refuses to start.
- Keep indentation exact: `services:` (0) → service name (2 spaces) → `image:`/`ports:`/`environment:` (4 spaces) → `- VAR=...` (6 spaces).
- Keep `8080:80` quoted as `- "8080:80"` if your Compose version warns about port parsing, though `- 8080:80` works in the lab file.
