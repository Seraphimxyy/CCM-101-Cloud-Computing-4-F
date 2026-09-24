# Laboratory 05 – Cloud Data Engineer

*Rogelio A. Mende (Seraphimxyy) – BSIT 4F – CCM-101 Cloud Computing*
*Mission 5: The Cloud Data Engineer – CloudNova Technologies*

## Mission Overview

This mission shifts focus from running servers to keeping data alive beyond them. A client building a photo-sharing application needs storage for millions of user uploads, but a web-server container cannot hold those files because containers are ephemeral — once removed, everything inside disappears.

As a reassigned Cloud Data Engineer at CloudNova Technologies, I built a proof-of-concept S3-compatible object storage service using MinIO on Docker. The work covers theory (Block vs File vs Object storage), deployment of MinIO on a KillerCoda Ubuntu Playground, browser access through port forwarding, creation of a `client-photos` bucket, and a test upload to prove durability and accessibility.

## Objectives

- Differentiate Block, File, and Object Storage by structure, use case, and provider example
- Deploy MinIO, an S3-compatible object storage server, using Docker with environment variables
- Access the MinIO Console via port forwarding on port 9001
- Create a bucket named `client-photos` and upload a test object
- Document deployment steps clearly in Markdown with screenshot evidence
- Maintain a structured GitHub Cloud Computing Portfolio

## Tools Used

- **KillerCoda Ubuntu Playground** – ephemeral Linux environment for Docker practice
- **Docker Engine** – container runtime for pulling and running `minio/minio`
- **MinIO (S3-compatible)** – object storage server with API on port 9000 and Web Console on port 9001
- **Modern Web Browser + KillerCoda Traffic/Ports tab** – to open the MinIO Console outside the terminal
- **Git + GitHub** – portfolio repository `CCM-101-Cloud-Computing-4-F`
- **Markdown** – documentation format for all deliverables

## Skills Learned

- Explaining why flat, metadata-rich object storage scales better than hierarchical or block systems for media
- Running a stateful-feeling service in Docker with `-d`, `-p`, `--name`, `-e`, and `--console-address`
- Separating API traffic (9000) from admin console traffic (9001) and using port forwarding
- Performing admin tasks: login with root credentials, create bucket, set naming, upload object, verify listing
- Structuring lab documentation so another engineer can reproduce the deployment from commands alone
- Handling credentials responsibly and understanding why MinIO root keys must be long and private

## Repository Structure

```
Laboratory-05-Cloud-Data-Engineer/
├── README.md
├── storage-types-research.md
├── minio-deployment.md
├── reflection.md
└── screenshots/
    ├── minio-deployed.png
    └── minio-bucket-upload.png
```

## Screenshot Evidence

- `screenshots/minio-deployed.png` – terminal showing `docker run` success and `docker ps` with `minio-server` running
- `screenshots/minio-bucket-upload.png` – MinIO Console showing the `client-photos` bucket with uploaded test file

> Note: Screenshots are captured manually from KillerCoda and committed per checkpoint to keep history clean.

## Quick Reproduce

```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server \
-e "MINIO_ROOT_USER=cloudadmin" \
-e "MINIO_ROOT_PASSWORD=CloudNova2026!" \
minio/minio server /data --console-address ":9001"

docker ps
docker logs minio-server
```

Then open port `9001` via KillerCoda Traffic/Ports, log in, create bucket `client-photos`, and upload a file.

## Author

Rogelio A. Mende – BSIT 4F – GitHub: [@Seraphimxyy](https://github.com/Seraphimxyy/CCM-101-Cloud-Computing-4-F)
