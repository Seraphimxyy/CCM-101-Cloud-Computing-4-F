# Mission Reflection

##1. Which cloud infrastructure component do you think is the most important? Why?

Of the four core components compute, storage, networking, and the operating system I consider compute the most critical, since every other layer exists to support it. Storage is meaningless without a processor to read or write to it, and networking has no purpose if there is no running system to connect to. During my investigation using lscpu, I observed that the provisioned instance had only a single CPU core. This immediately clarified how constrained cloud resources can be by default, and how any compute-intensive task would bottleneck the entire system regardless of how much storage or bandwidth was available. If compute is misconfigured or insufficient, every other component becomes effectively useless, since there is nothing to execute processes, serve requests, or manage resources.

##2. How does Linux support cloud computing?

Linux is the backbone of most cloud infrastructure because it is open source, lightweight, and highly scriptable, making it ideal for the fast, automated, and cost-efficient environments that cloud providers require. Unlike proprietary operating systems, Linux can be freely modified and stripped down to minimal footprints, reducing overhead on virtual machines. This was evident in my own exploration: lscpu allowed me to inspect the virtual CPU architecture, free -h revealed how memory was allocated and used in human-readable form, and df -h showed disk utilization across mounted filesystems, including a 19 GB root partition. These commands demonstrated how Linux exposes system internals through simple, scriptable tools — a transparency that enables automation, monitoring, and rapid provisioning at scale, which is essential for cloud environments.

##3. Why is technical documentation important before deploying infrastructure?

Technical documentation ensures continuity and accountability. Reviewing my own README.md and infrastructure-report.md, I believe a colleague or senior engineer could reasonably understand the environment setup, the commands executed, and the reasoning behind key decisions. However, I also recognized gaps — certain configuration choices were not fully justified, which could confuse someone unfamiliar with the project. Incomplete documentation risks miscommunication, duplicated effort, and costly misconfigurations during deployment, especially in team settings where infrastructure decisions must be traceable.

##4. What new skills did you learn during this laboratory activity?

I learned to interpret raw system specifications rather than simply executing commands. For instance, I practiced identifying CPU core count and architecture through lscpu, calculating memory usage percentages from free -h output, and reading disk partition sizes and usage percentages from df -h. I also gained experience structuring Markdown documentation with headers, code blocks, and tables to present technical findings clearly, and troubleshooting a permission-denied error when attempting to write to a restricted directory, which taught me to check ownership and use sudo appropriately rather than blindly escalating privileges.

##5. How has your GitHub portfolio improved after completing this mission?

Previously, my portfolio consisted of a single README file with minimal technical substance. It now contains a structured folder with multiple documented deliverables, including an infrastructure report, an architecture diagram, screenshots of command outputs, and a meaningful commit history showing incremental progress. This progression reflects growth from simply describing projects to demonstrating verifiable, hands-on technical work a shift that better represents the practical skills expected of a cloud engineer.
