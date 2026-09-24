# Screenshots – What to Capture

This folder must contain 2 PNG files for Mission 5 evidence:

1. `minio-deployed.png`
   - KillerCoda terminal after running the `docker run ... minio/minio` command
   - Must also show `docker ps` output with `minio-server` status `Up` and ports 9000, 9001
   - How: run `docker ps` then use KillerCoda screenshot / OS Snipping Tool, save with this exact name

2. `minio-bucket-upload.png`
   - MinIO Web Console (port 9001) logged in as `cloudadmin`
   - Must show left menu → Buckets → `client-photos` open, with your uploaded test file visible in the object list
   - How: open port 9001 via Traffic/Ports tab, create bucket, upload file, screenshot the bucket view

Delete this guide file before final push, or keep it – but the two PNGs above are required for full marks.
Do not reuse classmates' screenshots; take your own so timestamps and IDs match your session.
