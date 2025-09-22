# 🌐 Cloud Computing Overview

Cloud computing delivers **on-demand IT resources** (servers, storage, databases, networking, analytics, software) over the internet with **pay-as-you-go pricing**.  

Instead of large upfront investments in hardware, organizations can **provision exactly the right type and size of resources** and scale as needed.  

---

## 🚀 Key Benefits of Cloud Computing

- **No large upfront investments** → Trade **capital expenses (CapEx)** for **variable expenses (OpEx)**.  
- **Elasticity & Scalability** → Scale up/down to match demand, avoid idle resources or shortages.  
- **Massive economies of scale** → Lower costs by leveraging cloud providers’ global infrastructure.  
- **Speed & Agility** → Provision resources in minutes instead of weeks.  
- **Focus on innovation** → Stop managing data centers, focus on differentiating projects.  
- **Global reach** → Deploy worldwide in just a few clicks.  
- **Disaster recovery & backup** → Reliable redundancy for business continuity.  
- **Developer support** → Tools and environments for faster innovation.  
- **Industry use cases** → Gaming, big data analytics, AI/ML, IoT, enterprise IT.  

---

## 🏗️ Types of Cloud Computing Service Models

### 1. **Infrastructure as a Service (IaaS)**
- **What it is**: Basic building blocks (compute, storage, networking).  
- **Who manages**: Customer manages OS, middleware, apps; provider manages physical infrastructure.  
- **Benefits**: High flexibility & control.  
- **Examples**: AWS EC2, Azure Virtual Machines, Google Compute Engine.  

---

### 2. **Platform as a Service (PaaS)**
- **What it is**: Pre-configured environment for developing, running, and managing applications.  
- **Who manages**: Provider manages infrastructure, OS, runtime, patching; customer focuses on apps and data.  
- **Benefits**: Speed up development, reduce overhead, handle patching and scaling automatically.  
- **Examples**: AWS Elastic Beanstalk, Google App Engine, Azure App Service.  

---

### 3. **Software as a Service (SaaS)**
- **What it is**: Fully managed applications delivered via the internet.  
- **Who manages**: Everything is managed by the provider; user just consumes the app.  
- **Benefits**: No installation, maintenance, or infrastructure concerns.  
- **Examples**: Gmail, Salesforce, Microsoft 365.  

---

## ☁️ Cloud Deployment Models

1. **Cloud**  
   - Fully deployed in the cloud.  
   - Either built natively in cloud or migrated from on-premises.  

2. **Hybrid**  
   - Connect on-premises infrastructure with cloud resources.  
   - Allows sensitive workloads to stay local while leveraging cloud scalability.  

3. **On-Premises (Private Cloud)**  
   - Deployed within an organization’s own data centers.  
   - Uses virtualization and resource management tools.  
   - Offers dedicated resources and higher control but less scalability.  

---

## 🌍 Global Infrastructure (Example: AWS)

- **Global Reach**: AWS serves **1M+ active customers** in **190 countries**.  
- **Regions**: Physical locations worldwide (20+ AWS regions).  
- **Availability Zones (AZs)**:  
  - Each region has multiple AZs (currently 60+).  
  - Each AZ = independent data center with redundant power, networking, and connectivity.  
  - AZs are **isolated failure zones** but connected with **low-latency links** for resiliency.  
- **Design Benefits**:  
  - High availability & fault tolerance.  
  - Flexibility to place workloads across multiple regions and AZs.  
  - Disaster recovery & compliance support.  

Each availability zone is treated as indepent failure zone, physically separated and located in lower risk flood plains
