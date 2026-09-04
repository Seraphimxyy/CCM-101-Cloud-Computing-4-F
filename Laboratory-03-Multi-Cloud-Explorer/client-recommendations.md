# Client Recommendations

## Client A - Startup / limited budget, rapid growth
Recommended: GCP

Why (3-5 sentences): Startup needs zero upfront cost, scale-to-zero, and speed over breadth. GCP gives $300 credits + always-free tier, Cloud Run/Functions that bill only when used, and simple projects/billing to avoid surprise bills. BigQuery + Firebase let a tiny team ship app + analytics without ops. If they hyper-scale later they can add GKE or multi-cloud, but GCP keeps burn lowest at start.

Services (3): Cloud Run (scale-to-zero containers), Cloud Storage + BigQuery (app data + analytics), Cloud IAM + Billing budgets.

## Client B - University on Windows/M365/AD
Recommended: Azure

Why: Campus already lives on Windows, AD, M365/Teams. Azure reuses those logins via Entra ID + SSO, same compliance and student licensing, and hybrid with on-prem labs via Arc/ExpressRoute. Staff already know PowerShell/Visual Studio, so training cost is lowest. No reason to re-platform identity.

Services: Entra ID + M365 SSO, Virtual Machines / App Service for .NET + Azure SQL Database, Blob Storage + VNet.

## Client C - AI Research HPC
Recommended: GCP

Why: Research needs GPUs/TPUs, batch scale, and Kubernetes without ticket queues. GCP was built for this: GKE (Google created K8s), Batch + Spot VMs for cheap large runs, BigQuery/Vertex AI for data + training. Global VPC + Cloud Storage give fast data to compute anywhere. Azure (OpenAI/HPC SKUs) is close second if lab is Microsoft-funded.

Services: GKE + Batch / Compute Engine with GPUs/TPUs, Cloud Storage + BigQuery, Vertex AI / Model Garden.

## Client D - Global E-commerce scale
Recommended: AWS

Why: Global shop needs most regions, edge caching, and proven Black-Friday scale. AWS has 39 regions / 750+ POPs, CloudFront + ALB + Auto Scaling, Aurora/RDS Multi-AZ for orders, and EKS/Lambda for peak bursts. Widest marketplace + partner ecosystem for payments/fraud. Pay-as-you-go handles seasonal spikes without over-provisioning.

Services: EC2 / EKS + ALB Auto Scaling, S3 + CloudFront + VPC, RDS Aurora Multi-AZ + ElastiCache.

## Checkpoint 6 - Decision Matrix
| Business Requirement | Recommended Platform | Justification |
|---|---|---|
| Startup | GCP | Lowest start cost, scale-to-zero, free credits, ship fast with small team |
| Enterprise | AWS | Broadest services + regions, proven at scale, most compliance/partners |
| Microsoft Env | Azure | Native AD/M365/.NET/SQL, hybrid with Arc, reuses licenses |
| AI/ML | GCP | TPUs/GPUs, Vertex, BigQuery, data-to-AI pipeline simplest |
| Kubernetes | GCP (GKE) | Google created K8s, GKE most mature, Autopilot option |
| Global Web App | AWS | Most regions + CloudFront edge, ALB + Aurora global scale |
