# Reflection

## 1. Most impressive platform + why
GCP impressed me most for developer experience - projects, global VPC, and BigQuery/Cloud Run remove so much plumbing that a solo dev can ship like a team. Standout feature: BigQuery (serverless SQL over TBs) + Cloud Run scale-to-zero; AWS breadth is unmatched but GCP is the fastest from idea to URL. Azure wins only when you already live in Microsoft-land.

## 2. Similarities among AWS/Azure/GCP
All three converge on the same building blocks: VMs for lift-and-shift (EC2 / Azure VMs / Compute Engine), object storage for unstructured data (S3 / Blob / Cloud Storage), managed relational DBs (RDS / Azure SQL / Cloud SQL), centralized identity with RBAC (IAM / Entra ID / Cloud IAM), and managed Kubernetes (EKS / AKS / GKE). All use regions + zones for HA/DR, pay-as-you-go with free tiers and budgets, and the same three control planes: web console + CLI + IaC (CloudFormation/Bicep/Terraform).

## 3. How requirements drive choice
Requirements beat preferences: startup with burn constraints -> GCP (credits, scale-to-zero, tiny ops); university on Windows/M365/AD -> Azure (reuse Entra SSO/licenses, Arc for labs, compliance); AI/HPC research -> GCP (TPUs, GKE, Batch + Spot, Vertex/BigQuery for data gravity); global e-commerce -> AWS (39 regions + 750+ edge POPs, CloudFront + ALB + Aurora Global). Change latency, residency, or RTO/RPO and the winner flips - that is the consultant lesson.

## 4. What you learned as consultant
I learned to diagnose before prescribing: 1) where is identity (AD vs greenfield), 2) what are RTO/RPO + residency, 3) where is data + who pays for egress. I also learned to size from evidence (Lab 03: 1 vCPU / 1.9GB / 20GB -> t3.small / B1ms / e2-small, not m5.large) and to present trade-offs in a decision matrix so a non-technical client can sign off. Cost, ops burden, and hiring pool matter as much as tech specs.

## 5. How portfolio improved
Before: flat notes. Now: portfolio-grade repo - `aws|azure|gcp-research.md` for evidence, `comparison.md` + `recommendations.md` for judgment, `linux-investigation.md` with OS/CPU/Mem/Disk screenshots for hands-on proof. Small atomic commits (`docs: add azure regions`), consistent `screenshots/` naming, tables + sources with accessed dates, and this reflection. A reviewer can trace claim -> source -> screenshot in 2 minutes.
