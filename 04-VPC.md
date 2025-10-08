# 🧭 AWS Core Networking & Compute Overview

## ☁️ Amazon VPC (Virtual Private Cloud)

Amazon VPC lets you provision a **logically isolated section of the AWS Cloud** where you define your own virtual network.

You control:
- IP address ranges  
- Subnets  
- Route tables  
- Network gateways  
- IPv4 and IPv6 connectivity  

---

### 🔑 Analogy

| Concept | Analogy |
|----------|----------|
| **Region** | State |
| **Availability Zone (AZ)** | City |
| **VPC** | Neighborhood |
| **Internet Gateway** | Gate to neighborhood |
| **Security Group** | Keypad/lock to the house |
| **Subnet** | Part of the neighborhood |
| **IP Address** | Street address |
| **EC2 Instance** | The house |

---

### 🏗️ Key Concepts

- **Availability Zones:** Physically separate data centers within a region.  
  Launching across multiple AZs improves resilience.
- **Subnets:** Logical subdivisions of a VPC’s IP range (CIDR block).  
  - **Public Subnet:** Routed to an Internet Gateway.  
  - **Private Subnet:** No Internet Gateway route.  
  - **VPN-Only Subnet:** Routed through a Virtual Private Gateway (Site-to-Site VPN).

---

### 🗺️ Route Tables

- Contain **routes** determining where network traffic goes.  
- Each subnet must be associated with **one** route table (though one table may serve multiple subnets).  

---

## 🖥️ Amazon EC2 (Elastic Compute Cloud)

Provides **scalable virtual servers** in the AWS cloud.

### ⚙️ Capabilities
- Launch and manage any number of virtual machines.  
- Configure compute, networking, and storage.  
- Scale up or down based on demand.  
- Pay-as-you-go — no upfront hardware costs.

### 📈 Benefits
- Elastic capacity for unpredictable workloads.  
- Integrated with AWS networking (VPC, Security Groups, Elastic IP).  
- Foundation for deploying most AWS applications.  
- [AWS EC2 Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

---

## 🌐 Amazon CloudFront (Content Delivery Network)

A **global CDN** that delivers data, videos, applications, and APIs securely with **low latency** and **high transfer speeds**.

### ⚡ Key Features
- Integrated with AWS global infrastructure.  
- Works seamlessly with:
  - **AWS Shield** → DDoS mitigation  
  - **Amazon S3 / EC2 / Elastic Load Balancing** as origins  
  - **Lambda@Edge** → Run code close to users for custom experiences  
- Ideal for **frequently accessed static content** (images, videos, software downloads).

---

## 🧭 Amazon Route 53 (DNS & Domain Management)

**Domain Name System (DNS)** translates human-readable domain names into IP addresses computers use.

### 🧱 Core Functions
- **DNS Resolution:** Maps `example.com` → `192.0.2.1`.  
- **Domain Registration:** Purchase and manage domain names.  
- **Health Checks:** Route traffic only to healthy endpoints.  
- **Traffic Routing:**  
  - To AWS resources (EC2, ELB, S3)  
  - Or external infrastructure  

### 🚀 Benefits
- Highly available and scalable DNS service.  
- Cost-effective global routing for internet applications.  
- Supports routing policies (simple, weighted, failover, geolocation).

---

**End of Notes**
