# Multi-Tier Architecture – Two-Tier Nextcloud Deployment

*Rogelio A. Mende (Seraphimxyy) – BSIT 4F – CCM-101 Mission 6 – CloudNova Technologies*

This document describes the architecture used for the university private-cloud proof-of-concept: Nextcloud + MariaDB deployed as two linked containers with Docker Compose.

## What is Two-Tier Architecture?

A Two-Tier Architecture splits an application into two separate layers (tiers) that run independently but communicate over a network:

```text
[ Tier 1: Web / Application ]  <--HTTP :8080-->  [ User Browser ]
        |
        |  SQL via internal Docker network (MYSQL_HOST=database)
        v
[ Tier 2: Database ]
```

Instead of packing everything into one container, each tier gets its own container, image, lifecycle, and scaling rules, all defined in one `docker-compose.yml`.

## The Web / Application Tier: Nextcloud (`app` service)

**Role:** Serve the user interface and handle HTTP requests.

- Runs the `nextcloud` image, mapped as `8080:80` so the KillerCoda host port 8080 reaches container port 80.
- Renders the private-cloud UI, file uploads/downloads, sharing links, and setup wizard.
- Holds application logic but **does not** permanently store user accounts or file metadata by itself — it forwards those reads/writes to the database tier.
- Stateless in design: it can be stopped, replaced, or updated without losing university data, as long as the database tier is intact.

## The Database Tier: MariaDB (`database` service)

**Role:** Store persistent data such as user accounts and file metadata.

- Runs the `mariadb:10.6` image with `MYSQL_DATABASE=nextcloud_db`, `MYSQL_USER=nextcloud_user`, and passwords set via environment variables.
- Persists tables for users, passwords, shares, and file indexes that Nextcloud queries on every login and file operation.
- Not exposed to the browser — only the `app` container talks to it over the internal Compose network.
- This is the stateful part of the system that must be kept safe and backed up.

## Why Separate Them?

It is better to have the web server and the database in two separate containers rather than packing them both into one because each tier has a different lifecycle and resource need: the web tier can be restarted, scaled, or upgraded without risking the database, while the database can be backed up, tuned, and secured independently. Separation also follows the single-responsibility principle — if Nextcloud crashes, MariaDB keeps data safe, and if the database needs maintenance, the web UI failure is isolated and easier to diagnose, making the whole stack more reliable, portable, and maintainable as Infrastructure as Code.

## Summary for the Client

| Concern | Single Container (Bad) | Two Containers with Compose (Good) |
|---|---|---|
| Failure isolation | Web bug can corrupt DB | Web crash does not lose DB data |
| Updates | Must rebuild everything | Update `app` or `database` image separately |
| Reuse | Locked together | MariaDB pattern reusable for other apps |
| Deployment | Long manual `docker run` chain | One file + `docker-compose up -d` |
