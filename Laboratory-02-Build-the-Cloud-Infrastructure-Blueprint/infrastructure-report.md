# Infrastructure Report

## Environment Investigation

| Item | Command Used | Finding |
| --- | --- | --- |
| Operating System | cat /etc/os-release | Ubuntu 24.04.4 LTS (Noble Numbat) |
| Kernel Version | uname -r | 6.8.0-136-generic |
| CPU Model | lscpu | Intel Xeon E312xx (Sandy Bridge, IBRS update) |
| Number of CPU Cores | lscpu | 1 |
| Total RAM | free -h | 1.9Gi |
| Disk Capacity | df -h | 19G (/dev/vda1, mounted on /) |
| Mounted File Systems | mount | /, /boot, /boot/efi, /run, /dev, /dev/shm |
| Hostname | hostname | ubuntu |
| IP Address | ip a / hostname -I | 172.30.1.2 |

## Screenshots

![Server Information](./screenshots/server-information.png)

![Storage Information](./screenshots/storage-information.png)

![Network Information](./screenshots/network-information.png)
