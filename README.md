# Vpc-Architecture-
# 🔐 Secure Virtual Private Cloud (VPC) Architecture on AWS

## 📌 Project Title:
**Designing a Secure VPC Architecture with Public and Private Subnets on AWS**

---

## 🎯 Objective

To design and deploy a secure Virtual Private Cloud (VPC) infrastructure on AWS using public and private subnets. This includes:

- Hosting a **Bastion Host** in a public subnet for secure SSH access
- Deploying a **Web Server** in a private subnet
- Using a **NAT Gateway** for internet access from private subnet
- Implementing proper **route tables**, **security groups**, and **network ACLs**

---

## 🧱 Architecture Overview

VPC: 10.0.0.0/16 ├── Public Subnet (10.0.1.0/24) │   ├── Bastion Host (EC2) │   └── NAT Gateway └── Private Subnet (10.0.2.0/24) └── Web Server (EC2)

---

## 🧰 Technologies Used

- AWS VPC
- Subnets (Public & Private)
- Route Tables
- Internet Gateway
- NAT Gateway
- Amazon EC2
- Security Groups
- Network ACLs (optional)
- Apache Web Server

---

## 🛠️ Key Components

| Component        | Description |
|------------------|-------------|
| **VPC**          | Isolated network with CIDR 10.0.0.0/16 |
| **Subnets**      | Public for Bastion, Private for Web Server |
| **Internet Gateway** | Enables internet access for public subnet |
| **Route Tables** | Routes for both subnets configured |
| **NAT Gateway**  | Enables internet access for private subnet |
| **Security Groups** | Firewalls controlling access |
| **EC2 Instances**| Bastion (SSH) and Web Server (HTTP) |

---

## 🚀 Step-by-Step Setup

### 1. Create a VPC
- CIDR block: `10.0.0.0/16`

### 2. Create Two Subnets
- Public: `10.0.1.0/24`
- Private: `10.0.2.0/24`

### 3. Setup Internet Gateway
- Attach to the VPC
- Route `0.0.0.0/0` from public route table

### 4. Setup NAT Gateway
- Allocate Elastic IP
- Place in public subnet
- Route `0.0.0.0/0` from private subnet to NAT

### 5. Launch EC2 Instances
- **Bastion Host** in public subnet (with public IP)
- **Web Server** in private subnet (no public IP)

### 6. Configure Security Groups
- Bastion: SSH from your IP
- Web Server: SSH and HTTP from Bastion only

### 7. Connect to Private EC2
- SSH into Bastion
- Then SSH into Web Server from Bastion

### 8. Host a Web Page
```bash
sudo yum install httpd -y
sudo systemctl start httpd
echo "<h1>Hello Kamran</h1>" > /var/www/html/index.html


---

✅ Verification Checklist

[x] Bastion Host SSH working

[x] NAT Gateway allows internet access to private subnet

[x] Web Server only accessible through Bastion

[x] Apache Web Server running inside private EC2

[x] Curl command verifies page from Bastion



---
