# Mission Reflection – Becoming a Cloud-Native Engineer

Deploying my first Docker container felt completely different from working with Virtual Machines. Installing an OS on a VM takes 15-30 minutes plus additional time for updates, web server installation, and configuration, with boot times measured in minutes because a full kernel must load. In contrast, `docker pull nginx` and `docker run -d -p 8080:80 --name my-nginx nginx` deployed a working Nginx web server in under 10 seconds, since containers share the host kernel and only start the application process.

I learned that port mapping `-p 8080:80` is necessary because containers are network-isolated by default. Nginx inside the container listens on its own private port 80, which is invisible from outside. Mapping host port 8080 to container port 80 creates a bridge so that `curl http://localhost:8080` on the host is forwarded into the container, allowing external access without exposing the container network directly.

Using `docker rm` taught me about container ephemerality. When I removed `my-nginx`, all data in its writable layer was permanently deleted, including logs and any files I might have created inside. Only data stored in volumes or committed to a new image survives, which means containers should be treated as disposable and stateless, with persistent data kept outside.

This changes DevOps collaboration profoundly. Developers can now package code with all dependencies into an image that runs identically on a laptop, in KillerCoda, or in production, eliminating it works on my machine problems. Operations teams no longer manually configure servers but orchestrate versioned services that scale in seconds, allowing both teams to share the same Dockerfile and deployment workflow.

My GitHub portfolio is evolving from theory to practice. Laboratories 01-03 documented cloud concepts and multi-cloud comparisons, while Laboratory 04 adds hands-on evidence: live CLI commands, terminal screenshots, and replicable procedures. It now demonstrates not just that I understand cloud-native ideas, but that I can deploy and manage real services, which is exactly what a Cloud-Native Engineer portfolio should prove.

*Word count: ~300 words*
