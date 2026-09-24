# Research: Types of Cloud Storage

*By Rogelio A. Mende (Seraphimxyy) – Laboratory 05, CloudNova Technologies*

Cloud storage is not one technology. The way data is split, named, and reached decides how fast an app grows, how much it pays, and how painful recovery becomes. Below is the three-way comparison I presented to our photo-sharing client.

## Comparison Table

| Aspect | Block Storage | File Storage | Object Storage |
|---|---|---|---|
| **Description (How does it store data?)** | Splits data into fixed-size raw blocks, each with its own address. The OS formats blocks with a filesystem (like NTFS/ext4) and treats them as a local drive. No built-in file names or folders at the storage layer. | Keeps data as files inside a shared hierarchical tree of folders and subfolders. Clients access it over network protocols such as NFS or SMB, with file locks and permissions controlling who edits what. | Stores each file as a self-contained object: the bytes + a unique ID/key + rich custom metadata. Objects sit flat inside a bucket (no true folder tree), reached over HTTP/S with a REST API. |
| **Primary Use Case** | High-speed, low-latency disks for databases, VM boot volumes, and transactional workloads where an OS needs to read and write small chunks constantly. | Team shares, home directories, legacy apps, and content pipelines where people expect drive letters, drag-and-drop folders, and simultaneous file editing. | Massive unstructured data: photos, videos, backups, logs, static website assets, and ML datasets where scale, durability, and direct web access matter more than in-place edits. |
| **Cloud Provider Example** | AWS Elastic Block Store (EBS), Azure Managed Disks, Google Persistent Disk | AWS Elastic File System (EFS), Azure Files, Google Filestore | AWS Simple Storage Service (S3), Azure Blob Storage, Google Cloud Storage — plus self-hosted S3-compatible MinIO used in this lab |

## Why Object Storage Fits the Client's Photo App

For a photo-sharing service expecting millions of uploads, object storage is the practical choice because every image becomes an independent object with its own URL, metadata tags (uploader, date, album), and unlimited bucket growth without repartitioning disks or untangling folder permissions. Unlike a single block volume tied to one VM, an object store stays reachable even if web containers restart, and it scales horizontally by adding nodes instead of buying a bigger hard drive.

*In short: block disks run the database, file shares help the team collaborate, but object buckets hold the product itself.*
