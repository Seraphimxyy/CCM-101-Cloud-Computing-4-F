# MinIO Deployment – S3-Compatible Object Storage on Docker

*Engineer: Rogelio A. Mende (Seraphimxyy) | Environment: KillerCoda Ubuntu Playground | Date: Mission 5*

This note records the exact steps I used to prove that a photo-sharing backend can live outside an ephemeral web container.

## 1. Exact Docker Command Used

```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server \
-e "MINIO_ROOT_USER=cloudadmin" \
-e "MINIO_ROOT_PASSWORD=CloudNova2026!" \
minio/minio server /data --console-address ":9001"
```

Breakdown of each part:

- `docker run -d` – start a new container in detached mode so it keeps running after the command returns.
- `-p 9000:9000` – maps the MinIO S3 API (host:container). Apps would upload/download images here.
- `-p 9001:9001` – maps the MinIO Web Console. Administrators use this in a browser.
- `--name minio-server` – gives the container a readable name for `docker ps`, `logs`, and `stop`.
- `minio/minio server /data` – image plus MinIO startup instruction to store all objects under `/data` inside the container.
- `--console-address ":9001"` – tells MinIO to serve its admin UI on port 9001 explicitly, avoiding random-port assignment.

Evidence: `screenshots/minio-deployed.png`

Verification commands I ran right after:

```bash
docker ps
docker logs minio-server
docker images | grep minio
```

Expected result: `minio-server` shows `STATUS: Up`, ports `0.0.0.0:9000->9000/tcp` and `0.0.0.0:9001->9001/tcp`, and logs print `API: http://...:9000` and `Console: http://...:9001`.

## 2. Port Used to Access the Web Console

**Port 9001**

Steps in KillerCoda:
1. Click the Traffic / Ports or Custom Ports panel.
2. Type `9001` and click Access / Open.
3. A new tab opens the MinIO Console login page.
4. Log in with `cloudadmin` / `CloudNova2026!`.

Port 9000 is reserved for S3 API calls (what the photo app code would use). Port 9001 is purely human administration, which keeps machine traffic and clicks separated.

## 3. Bucket Created

**Name: `client-photos`**

Steps in Console:
1. Left menu → Buckets → Create Bucket.
2. Enter `client-photos` (lowercase, no spaces – S3 naming rule).
3. Keep versioning/default settings for this proof-of-concept, then Create.
4. Open `client-photos` → Upload → select a safe sample file (e.g., `welcome-test.txt` or a small local image) → confirm.
5. Verify the object appears in the bucket listing.

Evidence: `screenshots/minio-bucket-upload.png`

Why this name: it isolates client media from future buckets like `client-thumbnails` or `client-backups`, and it matches what the app code would reference as its target bucket.

## 4. What the `-e` Flags Did

`-e` sets an **environment variable** inside the container at startup, without baking secrets into the image.

- `-e "MINIO_ROOT_USER=cloudadmin"` creates the initial admin username. MinIO refuses a default blank login; this seeds the account the console asks for.
- `-e "MINIO_ROOT_PASSWORD=CloudNova2026!"` creates the matching admin password. MinIO requires 8+ characters, so a long phrase satisfies its guardrail and protects the console from anonymous access.

Using `-e` instead of editing files makes the deployment repeatable: the same image can become a dev, staging, or demo server just by changing variables. In production I would not type the password in plain history – I would load it from a secret manager or `.env` file – but for this lab it demonstrates how containers receive configuration from the outside.

## Troubleshooting Notes

- `docker: port is already allocated` → another lab still holds 9000/9001. Run `docker ps`, then `docker stop minio-server` + `docker rm minio-server` and retry.
- Console blank / connection refused → the container mapped ports but KillerCoda port forwarding was not opened. Re-open port 9001 from the Traffic panel.
- `MINIO_ROOT_PASSWORD must be at least 8 characters` → short passwords are rejected on purpose; use the full `CloudNova2026!`.
- Upload fails → check the bucket name is exactly `client-photos` and the sample file is small (<5 MB) for a quick test.
