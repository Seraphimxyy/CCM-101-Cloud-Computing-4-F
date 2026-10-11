# Laboratory 06 – Cloud Deployment Engineer

*Rogelio A. Mende (Seraphimxyy) – BSIT 4F – CCM-101 Cloud Computing*
*Mission 6: The Cloud Deployment Engineer – CloudNova Technologies*

## Mission Overview

This mission moves from deploying single containers to deploying a complete multi-tier enterprise system using Infrastructure as Code (IaC). CloudNova Technologies has a new university client that wants to stop paying for Google Drive and host its own private, secure cloud storage.

As a Cloud Deployment Engineer, I deployed a proof-of-concept private cloud with **Nextcloud (web/application tier) + MariaDB (database tier)** linked together with **Docker Compose**. Instead of typing long `docker run` commands manually, the entire stack is defined in a single `docker-compose.yml` file and launched with one command: `docker-compose up -d`.

> A junior engineer deploys servers by typing commands; a senior engineer deploys infrastructure by writing code.

## Objectives

- Explain the concept of a multi-tier application architecture
- Understand the purpose and structure of a `docker-compose.yml` file
- Use a Linux command-line text editor (`nano`) to create configuration files
- Deploy a multi-container application (Nextcloud + MariaDB) using Docker Compose
- Document deployment procedures and Infrastructure as Code (IaC) principles using Markdown
- Continue expanding professional GitHub Cloud Computing Portfolio

## Tools Used

- **KillerCoda Ubuntu Playground** – ephemeral Linux environment with Docker
- **Docker + Docker Compose** – container runtime and multi-container orchestrator
- **Nextcloud (latest)** – enterprise private cloud storage web application, port `8080:80`
- **MariaDB 10.6** – relational database for user credentials and file metadata
- **nano** – CLI text editor for writing YAML
- **Modern Web Browser + KillerCoda Traffic/Ports tab** – to open Nextcloud setup page on port 8080
- **Git + GitHub** – portfolio repository `CCM-101-Cloud-Computing-4-F`
- **Markdown** – documentation format

## Commands Executed

```bash
# Checkpoint 3 - Write the Infrastructure Code
mkdir nextcloud-deployment
cd nextcloud-deployment
nano docker-compose.yml
# paste YAML, save with Ctrl+O, Enter, Ctrl+X

# Checkpoint 4 - Deploy the Multi-Container Stack
docker-compose up -d
docker-compose ps

# Checkpoint 5 - Teardown after browser verification
docker-compose down
