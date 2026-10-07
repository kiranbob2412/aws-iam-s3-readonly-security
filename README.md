cd ~/aws-iam-s3-readonly-security

cat > README.md <<'EOF'
# AWS IAM S3 Read-Only Security Platform

> **Enterprise-style AWS IAM security implementation demonstrating least-privilege access, MFA enforcement, explicit authorization boundaries, and CLI-based security validation.**

[![AWS](https://img.shields.io/badge/AWS-IAM%20%7C%20S3-orange?logo=amazonaws)](https://aws.amazon.com/)
[![Security](https://img.shields.io/badge/Security-Least%20Privilege-blue)](https://aws.amazon.com/iam/)
[![MFA](https://img.shields.io/badge/MFA-Enabled-success)](https://aws.amazon.com/iam/features/mfa/)
[![Status](https://img.shields.io/badge/Project-Verified-success)](#security-validation)

---

## Executive Summary

This project implements and validates a secure **AWS Identity and Access Management (IAM) architecture for controlled Amazon S3 read-only access**.

The objective is to provide an IAM identity with the minimum permissions required to inspect S3 resources while preventing unauthorized write and destructive operations.

The implementation combines:

- IAM group-based access control
- Customer-managed IAM policy
- Explicit authorization boundaries
- Multi-factor authentication (MFA)
- AWS CLI identity verification
- Positive and negative authorization testing
- Evidence-driven security validation
- Git-based infrastructure/security documentation

The result is a reproducible security control demonstrating the **AWS principle of least privilege**.

---

# Architecture

```text
                         AWS ACCOUNT
                    Account: 522798374865
                              │
                              │
                       ┌──────▼──────┐
                       │ IAM Group   │
                       │             │
                       │ S3-ReadOnly │
                       │   -Users    │
                       └──────┬──────┘
                              │
                              │ Membership
                              ▼
                    ┌──────────────────┐
                    │ IAM User         │
                    │                  │
                    │ s3-readonly-user │
                    └────────┬─────────┘
                             │
                             │ MFA
                             ▼
                    ┌──────────────────┐
                    │ MFA Device       │
                    │ ENABLED          │
                    └──────────────────┘

                             │
                             │ Group Policy
                             ▼
                ┌─────────────────────────┐
                │ Customer Managed Policy │
                │                         │
                │ s3-readonly-policy      │
                └────────────┬────────────┘
                             │
              ┌──────────────┴──────────────┐
              │                             │
              ▼                             ▼
       ┌──────────────┐              ┌───────────────┐
       │ ALLOWED      │              │ BLOCKED       │
       │              │              │               │
       │ ListAll      │              │ PutObject     │
       │ ListBucket   │              │ DeleteObject  │
       └──────┬───────┘              └───────┬───────┘
              │                              │
              ▼                              ▼
        Amazon S3                     Authorization
        Read Access                      Denied


---

# Author

**Kuchipudi Kiran Babu**

Cloud Engineer | AWS | Linux | DevOps | Cloud Security

This project was designed, implemented, tested, documented, and validated as part of my hands-on AWS Cloud Security engineering portfolio.

**GitHub:** https://github.com/kiranbob2412


# AWS IAM S3 Read-Only Security Platform

> Enterprise-style AWS IAM security implementation demonstrating least-privilege access, MFA enforcement, explicit authorization boundaries, and CLI-based security validation.

**Author:** Kuchipudi Kiran Babu  
**Role:** Cloud Engineer | AWS | Linux | DevOps | Cloud Security
