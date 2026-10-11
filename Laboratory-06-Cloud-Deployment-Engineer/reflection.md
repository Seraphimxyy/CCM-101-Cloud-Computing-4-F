# Mission Reflection – The Cloud Deployment Engineer

*Rogelio A. Mende (Seraphimxyy) – BSIT 4F – CCM-101 Mission 6*

Writing a `docker-compose.yml` file makes a cloud engineer's job easier because one versioned file replaces a chain of long manual commands. Instead of retyping `docker run` flags and environment variables for MariaDB and Nextcloud in the right order, I run `docker-compose up -d` and get the same network, DNS, and config every time. Sharing that file plus `ps` and `down` gives identical results, which is faster to audit, easier to push to GitHub, and true Infrastructure as Code.

I learned YAML is strictly space-sensitive, so a Tab instead of spaces breaks deployment. Compose fails fast with a parse error and no containers start, which taught me to use spaces only and validate before `up`. That strictness is frustrating at first, but it is what makes the file reliable.

We used environment variables like `MYSQL_PASSWORD`, `MYSQL_DATABASE`, `MYSQL_USER`, and `MYSQL_HOST` to configure containers without rebuilding images. They let the `database` service create `nextcloud_db`, and let the `app` service find it by name (`MYSQL_HOST=database`) with matching credentials. Changing a value means editing text, keeping images portable.

Deploying enterprise cloud storage in minutes felt empowering. Seeing Compose pull both images, then opening port 8080 to the real Nextcloud setup screen, proved two small definitions can replace a full server install. Running `docker-compose down` and seeing clean removal made multi-container work feel manageable.

Since Mission 1, my view shifted from cloud as rented servers to cloud as reproducible systems. From concepts to single containers to MinIO storage, I can now define, deploy, verify, and tear down a two-tier stack as code and document it in Markdown. That shift from typing commands to writing infrastructure is what readied me for the Deployment Team. (298 words)
