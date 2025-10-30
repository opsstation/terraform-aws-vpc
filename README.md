# 🏗️ Terraform-AWS-VPC

[![OpsStation](https://img.shields.io/badge/Made%20by-OpsStation-blue?style=flat-square&logo=terraform)](https://www.opsstation.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Terraform](https://img.shields.io/badge/Terraform-1.6%2B-purple.svg?logo=terraform)](#)
[![CI](https://github.com/OpsStation/terraform-aws-vpc/actions/workflows/ci.yml/badge.svg)](https://github.com/OpsStation/terraform-aws-vpc/actions/workflows/ci.yml)

> 🌩️ **A production-grade, reusable AWS VPC module by [OpsStation](https://www.opsstation.com)**
> Designed for reliability, performance, and security — following AWS networking best practices.
---

## 🏢 About OpsStation

**OpsStation** delivers **Cloud & DevOps excellence** for modern teams:
- 🚀 **Infrastructure Automation** with Terraform, Ansible & Kubernetes
- 💰 **Cost Optimization** via scaling & right-sizing
- 🛡️ **Security & Compliance** baked into CI/CD pipelines
- ⚙️ **Fully Managed Operations** across AWS, Azure, and GCP

> 💡 Need enterprise-grade DevOps automation?
> 👉 Visit [**www.opsstation.com**](https://www.opsstation.com) or email **hello@opsstation.com**

---
## 🌟 Features

- ✅ Creates AWS **VPC**, **route tables**, **IGW**, and **NAT gateways**
- ✅ Supports **multiple CIDR ranges** and **availability zones**
- ✅ Optional **VPC Flow Logs** with CloudWatch or S3 destination
- ✅ Configurable **DHCP options**
- ✅ Modular & production-ready layout
- ✅ Seamless integration with other OpsStation Terraform modules

---
## ⚙️ Usage Example
### 🧱 Basic VPC Example
```hcl
module "vpc" {
  source  = "opsstation/vpc/aws"
  version = "1.0.0"

  name        = "vpc"
  environment = "prod"
  cidr_block            = "10.0.0.0/16"
  additional_cidr_block = ["172.3.0.0/16", "172.2.0.0/16"]
  availability_zones     = ["us-east-2a", "us-east-2b"]
  public_subnet_cidrs    = ["10.0.1.0/24", "10.0.2.0/24"]
  private_subnet_cidrs   = ["10.0.3.0/24", "10.0.4.0/24"]
  enable_flow_log                     = true
  create_flow_log_cloudwatch_iam_role = true
  dhcp_options_domain_name         = "service.consul"
  dhcp_options_domain_name_servers = ["127.0.0.1", "10.10.0.2"]
}

```
### ☁️ Outputs (AWS VPC Module)

| Name                                   | Description                                                        |
|---------------------------------------|--------------------------------------------------------------------|
| `id`                                  | The ID of the VPC.                                                 |
| `tags`                                | A mapping of tags assigned to the VPC resource.                    |
| `vpc_cidr`                            | The primary IPv4 CIDR block of the VPC.                             |
| `vpc_ipv6_cidr_block`                 | The primary IPv6 CIDR block of the VPC.                             |
| `vpc_ipv6_association_id`             | The association ID for the primary IPv6 CIDR block.                 |
| `ipv6_cidr_block_network_border_group`| The Network Border Group Zone name for the IPv6 CIDR block.         |

---
### ☁️ Tag Normalization Rules (AWS)

| Cloud | Case      | Allowed Characters | Example                            |
|--------|-----------|------------------|------------------------------------|
| **AWS** | TitleCase | Any              | `Name`, `Environment`, `CostCenter` |

---

### 💙 Maintained by [OpsStation](https://www.opsstation.com)
> OpsStation — Simplifying Cloud, Securing Scale.

