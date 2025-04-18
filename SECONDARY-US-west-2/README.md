
# 🏗️ Terraform Infrastructure for Secondary Region (us-west-2)

This project provisions a cloud infrastructure in the secondary region (`us-west-2`) for the purpose of **multi-region deployment**, **disaster recovery**, or **read scaling**. It includes the following:

- VPC and networking setup
- EC2 auto scaling
- Load balancers for frontend and backend services
- RDS read replica from the primary region
- Bastion host for secure SSH access

---

## 📁 File Overview

### 🛠 Core Configuration

| File | Description |
|------|-------------|
| `provider.tf` | AWS provider setup for `us-west-2` region. |
| `launctemp.tf` | EC2 launch templates (recommended to rename to `launchtemplate.tf`). |

---

### 🚀 Compute & Autoscaling

| File | Description |
|------|-------------|
| `autoscalling.tf` | Auto Scaling Group configuration for EC2 instances in `us-west-2`. |
| `backend-lt.sh` | EC2 user data script for initializing backend servers. |
| `frontend-lt.sh` | EC2 user data script for initializing frontend servers. |

---

### 🎛️ Load Balancing

| File | Description |
|------|-------------|
| `backend-tg&lb.tf` | Load Balancer and Target Group for backend services. |
| `frontend-tg&lb.tf` | Load Balancer and Target Group for frontend services. |

---

### 🌐 Networking

| File | Description |
|------|-------------|
| `vpc.tf` | Virtual Private Cloud (VPC) setup, subnets, NAT gateways, route tables. |
| `security_group.tf` | Security group configurations for controlling network traffic. |
| `subnetgroup-rds.tf` | Defines subnet groups for RDS instances and replicas. |

---

### 💾 Database (Replication)

| File | Description |
|------|-------------|
| `read-replica.tf` | AWS RDS read replica creation in `us-west-2` from the primary region. |

---

## ✅ Getting Started

1. **Initialize Terraform:**
   ```bash
   terraform init
   ```

2. **Preview the plan:**
   ```bash
   terraform plan
   ```

3. **Apply the configuration:**
   ```bash
   terraform apply
   ```

4. **(Optional) Destroy resources:**
   ```bash
   terraform destroy
   ```

---

## 📂 Recommended Structure

```
SECONDARY-US-west-2/
SECONDARY-US-west-2/
├── scripts/
│   ├── backend-lt.sh             # User data script for backend EC2
│   └── frontend-lt.sh            # User data script for frontend EC2
├── autoscalling.tf               # Auto Scaling Group definitions
├── backend-tg&lb.tf              # Backend target group & load balancer
├── frontend-tg&lb.tf             # Frontend target group & load balancer
├── launctemp.tf                  # EC2 launch templates (rename to launchtemplate.tf)
├── provider.tf                   # AWS provider config (region = us-west-2)
├── read-replica.tf               # RDS Read Replica from primary region
├── security_group.tf             # Security group definitions
├── subnetgroup-rds.tf            # RDS subnet group for regional DB placement
├── vpc.tf                        # VPC, subnets, gateways, etc.
└── README.md                     # Secondary region documentation

```

---

## 📌 Notes

- ✅ Ensure AWS credentials are configured for `us-west-2` before running Terraform.
- ⚠️ File `launctemp.tf` may need to be renamed to `launchtemplate.tf`.
- 💬 Consider modularizing shared resources between regions if applicable.

---

## 📞 Contact

For questions, feedback, or contributions, feel free to reach out to the project maintainer.

