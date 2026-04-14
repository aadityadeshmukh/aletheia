
**Core Principle**

For systems rated C-grade (high confidentiality) with E-grade integrity controls, automated provisioning protocols like SCIM create unacceptable security gaps.

**Why SCIM Fails for C-Grade Data**

SCIM assumes receiving systems have strong integrity controls: tamper detection, immutable audit logs, anomaly detection. When both the source and SaaS provider have minimal integrity (E-grade), connecting them directly via SCIM creates a bidirectional attack surface.

Compromise scenario: An attacker intercepts provisioning traffic, creates unauthorized accounts, escalates permissions, or modifies user attributes. Neither system detects the tampering. The attacker gains access to sensitive data without leaving a detectable trail.

**Attack Vectors in SCIM for Low-Integrity Systems**

1. Traffic interception and user attribute tampering (undetected privilege escalation)
2. Credential compromise via SCIM tokens (persistent unauthorized access)
3. Privilege escalation on legitimate accounts (weaponizing trusted users)

Result: Unauthorized access to high-sensitivity data with no audit trail. Compliance and regulatory failures.

**Two Defensible Approaches**

**Manual Provisioning** Access request → human approval → manual account creation in SaaS. Slower, but every user is explicitly vetted and documented. Audit trail is permanent and visible. Works for any sensitivity level.

**Identity Governance Platform (e.g., Saviynt)** Acts as a controlled intermediary between source and SaaS provider. Enforces approval workflows, maintains immutable logs, detects anomalies. Only defensible if it adds real controls—approval gates, segregation of duties, real-time logging. Not just a wrapper around SCIM.

**General Rule**

Match provisioning method to system sensitivity. For C-grade + E-grade integrity, automated protocols without compensating controls are not acceptable. Manual or governance-layer approaches are required.