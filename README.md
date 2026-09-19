# AWS Cloud Security Engineering

**CloudFoxable Attack Path Analysis, Controlled Exploitation, Hardening, and Retesting**

This repository documents a hands-on AWS cloud security engineering project using [CloudFoxable](https://github.com/BishopFox/cloudfoxable), Bishop Fox's intentionally vulnerable AWS training environment.

The focus of this project is not simply completing CTF challenges. The goal is to approach the environment like a small cloud security engagement: begin from a constrained AWS identity, enumerate what that identity can reach, identify attack paths, validate their impact in the authorized lab, remediate the underlying weakness, and retest the original path.

> **Authorized lab only.** All testing is performed against intentionally vulnerable resources deployed in my own AWS account specifically for this project. No production or third-party systems are in scope.

## Project Goals

- Enumerate AWS resources and IAM relationships from a limited starting identity
- Identify at least four cloud weaknesses or attack paths
- Demonstrate each attack path through controlled exploitation
- Capture sanitized technical evidence
- Explain the technical and business impact
- Remediate the root cause using defensive cloud security practices
- Retest the original path to verify the remediation

## Environment

```text
Proxmox Home Lab
      |
      +-- Ubuntu LXC Security Workstation
              |
              +-- AWS CLI
              +-- Terraform
              +-- CloudFoxable AWS profile
                      |
                      v
                  AWS Account
                      |
                      +-- CloudFoxable intentionally vulnerable resources
```

**Tooling:** Proxmox, Ubuntu, AWS CLI, Terraform, AWS IAM, AWS STS, CloudFoxable

## Lab Setup

The AWS lab was deployed from an Ubuntu LXC in my Proxmox home lab. A dedicated deployment identity was used to provision CloudFoxable, while all attack-path testing begins from CloudFoxable's intended CTF starting identity.

The full installation process, commands, screenshots, and identity separation are documented separately so the main repository can stay focused on the security assessment itself.

### [View the Full Lab Setup Guide](setup/README.md)

## Assessment Workflow

```text
Enumerate
   |
   v
Identify Weakness
   |
   v
Validate Attack Path
   |
   v
Capture Evidence
   |
   v
Assess Impact
   |
   v
Remediate
   |
   v
Retest
```

A finding is not considered complete when exploitation succeeds. The final step is proving that the remediation prevents or materially restricts the original attack path.

## Findings

| Finding | Attack Path | Status |
| --- | --- | --- |
| 01 | In progress | Enumeration |
| 02 | Pending | Not started |
| 03 | Pending | Not started |
| 04 | Pending | Not started |

Completed technical write-ups will be added to the [findings directory](findings/).

## Current Status

| Stage | Status |
| --- | --- |
| Home lab assessment workstation | Complete |
| AWS CLI and Terraform tooling | Complete |
| CloudFoxable deployment | Complete |
| CTF starting identity verification | Complete |
| Attack-path enumeration | In progress |
| Four documented findings | Planned |
| Remediation and retesting | Planned |
| Business-facing security report | Planned |

## Finding Format

Each completed finding will document:

1. Security weakness
2. Discovery and enumeration
3. Attack path and controlled exploitation
4. Technical evidence
5. Technical impact
6. Business impact
7. Root cause
8. Remediation
9. Retest and proof of fix

A reusable template is available at [templates/finding-template.md](templates/finding-template.md).

## Repository Structure

```text
.
├── README.md
├── setup/
│   └── README.md
├── findings/
│   └── README.md
├── docs/
│   ├── assessment-plan.md
│   └── report-outline.md
├── remediation/
│   └── remediation-log-template.md
├── templates/
│   └── finding-template.md
└── media/
    └── screenshots/
```

## Repository Security

AWS account identifiers and other environment-specific values are redacted from public evidence. Terraform state, AWS credentials, private keys, variable files, and other secret-bearing artifacts are excluded from version control.

## Attribution

[CloudFoxable](https://github.com/BishopFox/cloudfoxable) is an intentionally vulnerable AWS training platform created and maintained by **Bishop Fox**. This repository contains my own deployment documentation, assessment evidence, attack-path analysis, remediation work, and reporting.
