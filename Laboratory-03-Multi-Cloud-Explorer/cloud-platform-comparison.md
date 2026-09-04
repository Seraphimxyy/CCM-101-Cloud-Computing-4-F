# Cloud Platform Comparison

## Comparison Table
| Category | AWS | Azure | GCP |
|---|---|---|---|
| Launch Year | 2006 (S3 Mar 2006, EC2 Aug 2006) | 2010 GA as Windows Azure (ann. 2008, renamed 2014) | 2008 App Engine preview / 2011 GA |
| Compute Service | EC2 | Virtual Machines | Compute Engine |
| Storage Service | S3 | Blob Storage | Cloud Storage |
| Networking Service | VPC | Virtual Network (VNet) | VPC (global) |
| Identity Service | IAM | Entra ID (ex-Azure AD) | Cloud IAM |
| Primary Strength | Broadest catalog, 200+ services, global scale | Microsoft-stack + hybrid + enterprise compliance | Data/AI + Kubernetes, simple global network |
| Ideal Organizations | Startups to enterprises needing anything at scale | Microsoft/Windows/.NET/M365 shops, regulated/hybrid | Data-driven, cloud-native, container/AI teams |

## Analysis (2-3 sentences each, your words)

### 1. Broadest range?
AWS. It has 200+ services and the largest region/AZ footprint (39 regions / 124 AZs), so for almost any workload there is a managed option. That breadth is why it leads in market share and jobs, but it also means a steeper learning curve.

### 2. Best Microsoft integration?
Azure, by far. Same Entra ID login for M365 + Azure, native support for Windows Server, SQL Server, .NET, Active Directory, plus Arc/ExpressRoute for hybrid. If you already pay for Microsoft licenses, Azure reuses them and feels like an extension of on-prem.

### 3. Strongest AI/Kubernetes?
GCP. Google created Kubernetes (so GKE is the reference), plus BigQuery for serverless analytics and Vertex/Gemini for AI. Azure is also very strong in AI via OpenAI partnership, and AWS has Bedrock/SageMaker, but GCP is the most Kubernetes- and data-native.

### 4. Your personal choice + why?
GCP for learning/personal projects, AWS for employability. I would start on GCP because projects, global VPC, and BigQuery/Cloud Run are simpler to reason about and the free tier ($300 + always-free) is generous. For client work I would default to AWS because its breadth and hiring demand cover the most use cases.

## Checkpoint 5 - Service Match
| Service Category | AWS | Azure | GCP |
|---|---|---|---|
| Virtual Machine | EC2 | Virtual Machines | Compute Engine |
| Object Storage | S3 | Blob Storage | Cloud Storage |
| Identity Management | IAM | Entra ID | Cloud IAM |
| SQL Database | RDS / Aurora | SQL Database | Cloud SQL |
| Kubernetes | EKS | AKS | GKE (created Kubernetes) |

## Sources
Accessed: 2026-09-04

- https://aws.amazon.com/what-is-aws/
- https://aws.amazon.com/about-aws/global-infrastructure/
- https://docs.aws.amazon.com/
- https://azure.microsoft.com/en-us/explore/global-infrastructure
- https://learn.microsoft.com/en-us/azure/reliability/regions-overview
- https://learn.microsoft.com/en-us/azure/azure-portal/azure-portal-overview
- https://cloud.google.com/docs/overview
- https://cloud.google.com/about/locations
- https://cloud.google.com/cloud-console
