# Virtual Machines vs. Containers

*CCM101 – Laboratory 04 – Research Report for CloudNova Technologies Client*

## Comparison Table

| Category | Virtual Machines (VMs) | Containers (Docker) |
|----------|------------------------|---------------------|
| **Architecture** | Each VM includes a full Guest OS on top of a Hypervisor. The Hypervisor virtualizes hardware for each VM. | Containers share the Host OS kernel. The Docker Engine virtualizes at the OS/process level, no Guest OS per app. |
| **Boot Time** | Minutes (2–5+ minutes). Must boot a full OS, load kernel, drivers, and system services. | Seconds (<5 seconds, often milliseconds). Only starts the application process, kernel is already running. |
| **Resource Efficiency** | Heavy / High RAM usage. Each VM needs GBs of RAM and disk (e.g., 2–4 GB RAM, 10–20 GB disk just for OS). Only a few VMs per host. | Lightweight / Low RAM usage. Images are MBs in size (e.g., Nginx ~187 MB). Dozens to hundreds of containers can run on the same host. |
| **Isolation Level** | Hardware-level isolation. Strong isolation via Hypervisor; each VM has its own kernel, very secure but heavy. | Process-level (OS-level) isolation. Uses namespaces and cgroups for isolation; lightweight but shares the same kernel, so slightly weaker isolation than VMs. |

## Summary for the Client

Your current Virtual Machines are slow to boot and waste RAM because each one carries a full operating system. Containers solve this by sharing the host OS kernel and packaging only your application and its dependencies, allowing them to start in seconds and use far less memory. For your web applications, this means faster deployments, lower cloud costs, and the ability to run many more services on the same server. Moving to Docker containers will let your IT team deploy and scale your Nginx web servers in seconds instead of 15+ minutes.

## Evidence

See `screenshots/` for terminal evidence of Docker deployment.
