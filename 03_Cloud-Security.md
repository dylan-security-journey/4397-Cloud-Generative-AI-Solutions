## Cloud Security

<img width="1378" height="823" alt="image" src="https://github.com/user-attachments/assets/4d80e3f4-a3f8-4f8b-8ee2-be771e5ad168" />

The customer is responsible for security in the cloud, while AWS is responsible for the security of the cloud

# What This IAM Setup Does (Markdown Notes)

## What IAM Is (Quickly)
**AWS Identity and Access Management (IAM)** lets you create identities (users/roles) and attach **policies** that define what those identities can and can’t do in your AWS account.

---

## What Your Procedure Accomplishes
1. **Stop using the root user for daily work**
   - Root = the “master key” to the entire account. Use it only to bootstrap, then lock it away.

2. **Enable IAM access to billing**
   - Turning on *“IAM User and Role Access to Billing”* lets non-root admins view/manage billing, budgets, and cost settings.

3. **Create an IAM user named `Administrator` (console sign-in)**
   - Dedicated username/password (add MFA). Managed by password policies and fully auditable via CloudTrail.

4. **Create an IAM group named `Administrators` and attach `AdministratorAccess`**
   - A group is a reusable permission container. Every member inherits the same permissions.
   - **`AdministratorAccess`** (AWS managed) effectively grants full access to all AWS services and resources.

5. **Add the `Administrator` user to the `Administrators` group**
   - This assignment is what actually grants full admin privileges to the user.

6. **(Optional) Tags and CSV**
   - **Tags** add metadata (owner, cost center, env) for governance/automation.
   - The **CSV** contains sign-in details to store securely or share if provisioning for someone else.

---

## Why Use Groups (vs. Attaching Policies Directly to a User)?
- **Scale & consistency:** One change to the group updates permissions for all members.
- **Governance:** Easy audits—“who are our admins?” = members of `Administrators`.
- **Best practice:** Prefer group- or role-based permissions over user-attached policies.

---

## What the `Administrator` User Can Do Now
- Create/modify/delete **any** AWS resource (EC2, S3, IAM, VPC, RDS, etc.).
- Manage **security settings** (policies, roles, keys, MFA requirements).
- Access **billing/cost** pages (because IAM billing access is enabled).
- Configure **org-wide logging/monitoring** (CloudTrail, CloudWatch, GuardDuty).
- Act as day-to-day **super-admin** without touching the root user.

---

## Security Implications & Best Practices
- **MFA everywhere:** Enable MFA for root and the `Administrator` user.
- **Least privilege for normal work:**
  - Use a separate low-privilege user/role for daily tasks.
  - Prefer **assume-role** escalation into an Admin **role** only when needed.
- **Avoid long-lived access keys** for human users; prefer roles/temporary creds.
- **Logging:** Ensure CloudTrail is enabled and writing to a secure, immutable S3 bucket (Object Lock/versioning).
- **Break-glass mindset:** Treat `AdministratorAccess` like emergency power—protected and well-audited.

---

## Simple Mental Model
- **Root** = master key (lock it up).
- **Admin user + Admin group** = everyday super-admin (with MFA & auditing).
- **Groups/Policies** = reusable permission sets.
- **Billing toggle** = lets admins manage costs without using root.

<img width="709" height="653" alt="image" src="https://github.com/user-attachments/assets/4e295d74-b164-46b1-afe7-44824c0c4dce" />

# IAM Core Concepts — Summary

## Quick Flow
**Principal → Request → Authentication → Authorization → Actions/Operations → Resources**

---

### Principal
- **Who/what acts:** A person or application that makes requests to AWS.
- **Best practice:** Don’t use the **root** user for daily work—use **IAM users** or **roles**.

### Request
- **What happens:** The principal uses the Console, API, or CLI to send a **request** to AWS (includes the action, target resource, and context like Region, time, source IP).

### Authentication
- **Proving identity:** The principal must **sign in** with valid credentials (password + MFA, access keys, or temporary creds via STS).

### Authorization
- **Permission check:** AWS evaluates **policies** that match the request context to decide **Allow** or **Deny** (explicit Deny overrides Allow).

### Actions / Operations
- **What you can do:** Service-defined operations (e.g., `s3:PutObject`, `ec2:StartInstances`) that the request is asking to perform.

### Resources
- **What is affected:** The specific AWS objects the action targets (e.g., an **S3 bucket**, an **EC2 instance**, an **IAM user**).

---

## One-Liner Example
> An IAM role (principal) calls `s3:GetObject` (action) on `arn:aws:s3:::my-bucket/report.csv` (resource).  
> AWS authenticates the role, evaluates attached policies (authorization), and—if allowed—returns the object.

## Logging & Monitoring — TL;DR

- **AWS CloudTrail:** Records every API call (incl. console/API, IAM, STS) as events for auditing.
- **IAM Access Analyzer:** Flags resources (e.g., S3 buckets, IAM roles) that are **public or shared externally**.
- **Amazon CloudWatch:** Real-time metrics/monitoring; build dashboards and set **alarms** that notify or trigger actions at thresholds.
- **CloudWatch Logs:** Central place to collect, store, and search logs from EC2, CloudTrail, and other sources.

**Soundbite:** CloudTrail = audit trail, Access Analyzer = exposure checks, CloudWatch = metrics/alerts, CloudWatch Logs = log storage/search.

## AWS Shield vs. Amazon GuardDuty — TL;DR

- **AWS Shield**  
  - Managed **DDoS protection** for apps on AWS.  
  - **Always-on** detection with **automatic inline mitigations** to reduce downtime/latency.  
  - Two tiers: **Standard** and **Advanced**.

- **Amazon GuardDuty**  
  - Continuous **threat detection** for malicious or unauthorized activity across your AWS environment (accounts, workloads, S3).  
  - Think of it as “**antivirus for your AWS account**.”

**Quick mental model:**  
Shield = stop external **DDoS floods**; GuardDuty = **spot bad behavior** inside your AWS signals.

## Security Best Practices — TL;DR

### 1) EBS Encryption
- Built-in encryption for **EBS volumes** (covers data at rest; can also encrypt boot volumes).
- No need to build your own key mgmt stack—use AWS-managed KMS keys (or your own CMKs if required).

### 2) Lock Down Root Account Credentials
- Root has full, irreversible power → **don’t use it for daily work**.
- Create an **IAM admin user/role** to manage the account instead.
- **Enable MFA** on root and admin identities; avoid root access keys entirely.

### 3) Keep All Servers Patched
- Patch every instance—even private/non-internet-facing ones.
- Use **AWS Systems Manager Patch Manager** to automate scheduling, approvals, and reporting.

---

### Quick Actions Checklist
- [ ] Turn on **default EBS encryption** for the account/Region.  
- [ ] Remove/rotate any **root access keys**; enable **MFA on root**.  
- [ ] Create an **Admin role**; use assume-role instead of long-lived admin users.  
- [ ] Enforce **MFA** and strong password policies for all users.  
- [ ] Set up **SSM Patch Manager** maintenance windows and baselines.  

**Soundbite:** Encrypt storage, lock down root, and patch continuously—with automation.






























































