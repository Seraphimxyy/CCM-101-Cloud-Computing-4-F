# Laboratory Activity 2: Build the Cloud Infrastructure Blueprint

## Mission Overview
This laboratory activity was designed to simulate the planning phase of a cloud deployment on behalf of a fictional company preparing to migrate its services to the cloud. Using a Linux server provisioned through the KillerCoda Playground, the environment was investigated in order to identify its underlying infrastructure components — compute, storage, networking, and identity. The equivalent services offered by three leading public cloud providers (Amazon Web Services, Microsoft Azure, and Google Cloud Platform) were then researched and compared, and a simple cloud infrastructure diagram was designed to illustrate the relationship between these components. All findings were documented in Markdown format and committed to the author's GitHub Cloud Computing Portfolio.

## Objectives
By the end of this laboratory activity, the following objectives were achieved:
- Explain the major components of cloud infrastructure.
- Investigate the hardware and software resources available within a Linux environment.
- Differentiate between compute, storage, networking, and identity resources.
- Interpret the relationship between cloud infrastructure components.
- Produce professional technical documentation using Markdown.
- Continue building a structured GitHub Cloud Computing Portfolio.

## Cloud Infrastructure Components

| Component | Purpose | Relation to the KillerCoda Environment |
| --- | --- | --- |
| **Compute** | Processes commands and performs the calculations required for the system to function. | The environment provided an Intel Xeon E312xx (Sandy Bridge) CPU with a single core. While limited compared to a production system, this is consistent with a free lab environment intended for command practice rather than production workloads. |
| **Storage** | Provides a reliable and accessible location for saving files and data. | A 19 GB disk (`/dev/vda1`) mounted at `/` serves as the primary storage volume for the server. |
| **Networking** | Enables machines to communicate rather than operate in isolation. | The server was assigned its own address (`172.30.1.2` on interface `enp1s0`), enabling it to send and receive data within the KillerCoda environment. |
| **Operating System** | Manages hardware resources and provides the interface through which the user interacts with the system. | The environment runs Ubuntu 24.04.4 LTS (Noble Numbat), kernel `6.8.0-136-generic`. |

## Tools Used
- **KillerCoda Playground** — provided the temporary Linux cloud server for investigation.
- **Linux terminal** — used to inspect system specs and infrastructure.
- **GitHub** — used to store and version the Cloud Computing Portfolio.
- **Canva** — used to design the cloud infrastructure diagram (Checkpoint 5).
- **Official AWS / Azure / GCP documentation** — used to research equivalent cloud services (Checkpoint 4).

## Linux Commands Executed

| Command | Purpose |
| --- | --- |
| `whoami` | Confirmed the logged-in user (root). |
| `git clone <repo-url>` | Cloned the GitHub Cloud Computing Portfolio repository. |
| `git config --global user.name / user.email` | Set up Git identity for commits. |
| `mkdir -p` | Created the lab folder structure, including the `screenshots` subfolder. |
| `touch` | Created the Markdown deliverable files. |
| `cat /etc/os-release` | Retrieved the operating system name and version. |
| `uname -r` | Retrieved the kernel version. |
| `lscpu` | Retrieved CPU model and core count. |
| `free -h` | Retrieved total RAM. |
| `df -h` | Retrieved disk capacity and usage. |
| `mount \| column -t` | Listed mounted file systems in a readable format. |
| `hostname` | Retrieved the server's hostname. |
| `ip a` / `hostname -I` | Retrieved the server's IP address(es). |

## Skills Learned
- Investigating a Linux server's hardware and software specifications using the command line.
- Relating low-level system information (CPU, RAM, disk, and network interface data) to higher-level cloud infrastructure concepts.
- Comparing equivalent services across AWS, Azure, and GCP using official documentation.
- Structuring and maintaining technical documentation in Markdown within a GitHub repository.

## Challenges Encountered
- Encountered incomplete sentences while drafting `cloud-components.md` in `nano`, which required manual review and correction before the file was finalized.
- A minor command syntax error (`cat /etc/os/-release` instead of `cat /etc/os-release`) initially returned a "No such file or directory" error and was corrected on the subsequent attempt.
- Continued to build familiarity with the underlying mechanics of cloud networking beyond simply identifying the assigned IP address.
