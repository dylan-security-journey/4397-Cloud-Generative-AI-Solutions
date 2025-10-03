# Cloud Security — Notes

**Date:**  
**Reader:** Dylan Nguyen  
**Context/Goal:** (e.g., prep for Entergy interview, refresh AWS security basics)

---

## 1) Cloud Security (Overview)
**Key idea (1–2 lines):**  
- 

**My takeaways:**  
- 

**Questions:**  
- 

---

## 2) AWS Shared Responsibility Model
**What AWS secures (provider-owned):**  
- 

**What the customer secures (you):**  
- 

**Borderline “shared” areas (clarify in interviews):**  
- 

**Example notes / mental model:**  
- 

---

## 3) AWS IAM — Overview
**Core concepts (in my words):**  
- **Principal:**  
- **Request:**  
- **Authentication:**  
- **Authorization:**  
- **Actions/Operations:**  
- **Resources:**  

**Policies/Scopes to remember:**  
- 

**Gotchas / interview soundbites:**  
- 

---

## 4) Create Administrator IAM User & Group (Console Walkthrough)
> Use this as a checklist while practicing in a sandbox account.

- [ ] Sign in as **root** only to bootstrap; lock away root creds after.  
- [ ] **Enable billing access** for IAM users.  
- [ ] Create IAM **user**: `Administrator` (console access; temp pw if desired).  
- [ ] Create **group**: `Administrators`; attach **AdministratorAccess** managed policy.  
- [ ] Add user → group; add **tags** (optional).  
- [ ] Download `.csv` / send login instructions (optional).  
- [ ] Turn on **MFA** for root and admins.  
- [ ] Confirm least-privilege approach for day-to-day users/roles.

**Notes from my run-through:**  
- 

---

## 5) IAM Console — Demo Notes
**What I clicked / observed:**  
- 

**Policies/roles I inspected:**  
- 

**Open questions / follow-ups:**  
- 

---

## 6) How IAM Works — Flow (My Words)
**Flow I’ll explain in an interview:**  
1) Principal sends a **request**  
2) **Authentication** → creds/session valid?  
3) **Authorization** → evaluate policies (allow/deny) using request context  
4) If allowed → perform **actions** on **resources**  
5) **Logging** records it (CloudTrail, etc.)

**Edge cases / denials I noticed:**  
- 

---

## 7) Logging & Monitoring
**Services to remember:**  
- **CloudTrail** — API activity/event history; org trails?  
- **IAM Access Analyzer** — finds external access paths to resources  
- **CloudWatch (metrics/alarms/dashboards)** — real-time health + automation  
- **CloudWatch Logs** — central log storage & search

**What I’d enable first in a new account:**  
- 

**Alert ideas / alarms worth setting:**  
- 

---

## 8) AWS Shield & GuardDuty
**AWS Shield (Standard vs. Advanced):**  
- 

**Amazon GuardDuty (threat detection):**  
- **Data sources (e.g., CloudTrail, VPC Flow, DNS):**  
- **Example findings to practice interpreting:**  

**Integration notes (alerts → response):**  
- 

---

## 9) Security Best Practices (From the Deck)
- **EBS Encryption** — data at rest (volumes/snapshots). Notes:  
  - 
- **Lock Down Root Credentials** — no access keys; MFA; break-glass only. Notes:  
  - 
- **Patch All Servers** — use **Systems Manager Patch Manager**. Notes:  
  - 

**My prioritized quick wins:**  
1)  
2)  
3)  

---

## 10) AWS Infrastructure Security Controls
**Docs/links I should skim:**  
- `https://aws.amazon.com/compliance/data-center/controls/`

**What matters for interviews (bullet my summary):**  
- 

---

## 11) Final Thoughts / “Thanks” Slide
**3–5 headline takeaways I’ll remember:**  
- 

**Gaps to research next:**  
- 

---

## Glossary (fill as you read)
- **Principal:**  
- **STS:**  
- **Managed Policy vs. Inline Policy:**  
- **Access Analyzer finding:**  
- **DDoS (Layer 3/4 vs. 7):**  

---

## Action Items
- [ ] Enable/verify **org-level CloudTrail** and log archive bucket  
- [ ] Create non-root **admin role**; enforce **MFA**  
- [ ] Baseline **GuardDuty** + alert routing  
- [ ] Review **EBS encryption** defaults & KMS key strategy  
- [ ] Set up **Patch Manager** maintenance windows

---

## Interview Snippets (prep answers)
**Explain IAM to a non-technical audience:**  
- 

**Shared Responsibility in one sentence:**  
- 

**How would you harden a new AWS account day 1?:**  
- 
