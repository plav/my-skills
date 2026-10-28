---
name: cloud-guide
description: Checklist for working with cloud platforms. Use when choosing or configuring cloud services, setting up IAM permissions, writing infrastructure as code, estimating or reducing cloud costs, or reviewing cloud security.
---

# Cloud

## Checklist
- Which managed service fits before building our own?
- IAM: least privilege for people and services
- Infrastructure defined as code, reviewed like code
- Cost estimated and monitored; budgets and alerts set
- Data encrypted at rest and in transit
- Backups and region/zone failure considered

## Core services (AWS / Azure / GCP names differ)
- Compute: VMs, containers, serverless functions
- Storage: object storage, block storage, file storage
- Databases: managed SQL and NoSQL
- Networking: VPC/VNet, subnets, load balancers, DNS
- IAM: users, roles, policies

## Infrastructure as code
- Terraform, CloudFormation, Bicep, Pulumi
- Repeatable environments; no manual console changes in production

## Cost
- Biggest costs: compute left running, data transfer, oversized resources
- Tag resources by team/project
- Turn off non-production environments when unused

## Shared responsibility
- Provider secures the cloud; you secure what you put in it (config, data, access)

## Further reading
- AWS Well-Architected: https://aws.amazon.com/architecture/well-architected/
- Azure Well-Architected: https://learn.microsoft.com/en-us/azure/well-architected/
- AWS shared responsibility model: https://aws.amazon.com/compliance/shared-responsibility-model/
