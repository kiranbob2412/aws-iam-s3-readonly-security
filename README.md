# AWS IAM S3 Read-Only Security

## Project Overview

This project demonstrates AWS IAM S3 read-only access using the principle of least privilege.

## IAM Configuration

- IAM User: s3-readonly-user
- IAM Group: S3-ReadOnly-Users
- IAM Policy: s3-readonly-policy
- MFA: Enabled

## Allowed Actions

- s3:ListAllMyBuckets
- s3:ListBucket

## Blocked Actions

- s3:PutObject
- s3:DeleteObject

## Verification

| Operation | Result |
|---|---|
| s3:ListAllMyBuckets | ALLOWED |
| s3:ListBucket | ALLOWED |
| s3:PutObject | BLOCKED |
| s3:DeleteObject | BLOCKED |
| MFA | ENABLED |
| Least Privilege | VERIFIED |

## Evidence

The docs directory contains IAM user, IAM group, policy assignment, and MFA evidence screenshots.

## Project Structure

aws-iam-s3-readonly-security/
- README.md
- policies/s3-readonly-policy.json
- docs/evidence-iam-user.png
- docs/evidence-iam-group.png
- docs/evidence-mfa.png
- docs/evidence-policy-assignment.png
- logs/cli-test-results.txt

## Skills

AWS IAM, Amazon S3, IAM Policies, MFA, AWS CLI, Least Privilege, Cloud Security, Git and GitHub.

**Project Status: VERIFIED**
