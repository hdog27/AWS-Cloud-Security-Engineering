# AWS Cloud Security Engineering — Attack Path Analysis, Exploitation & Hardening

This repository documents a hands-on **AWS cloud security engineering project** focused on cloud attack-path discovery, controlled exploitation, remediation, and retesting inside an **isolated, intentionally vulnerable lab environment** built with [CloudFoxable](https://github.com/BishopFox/cloudfoxable) by Bishop Fox.

## Project Summary

Rather than stopping at a hypothetical risk review, this project treats the environment like a small cloud security engagement:

- deploy a vulnerable AWS lab environment
- enumerate the environment from a low-privilege starting point
- identify at least four weaknesses or attack paths
- validate and document the findings
- explain the business impact in plain language
- remediate the underlying issues
- retest to confirm the fixes worked

## Scope and Ethics

- **Environment:** personal AWS account used only for this project
- **Target:** CloudFoxable, an intentionally vulnerable training environment
- **Purpose:** education, defensive analysis, remediation, and reporting
- **Out of scope:** any production systems, third-party assets, or unauthorized testing

## Current Status

- [x] Ubuntu LXC created in home lab
- [x] AWS CLI installed in the assessment container
- [x] Terraform initialized
- [x] CloudFoxable deployed in AWS
- [x] Initial evidence captured and sanitized
- [x] CloudFoxable CTF starting identity verified with AWS STS
- [ ] Four findings fully documented
- [ ] Remediation validation screenshots added
- [ ] Final business report completed

## Lab Architecture

```text
Home Lab / Proxmox
        │
        └── Ubuntu LXC (assessment workstation)
                ├── AWS CLI
                ├── Terraform
                └── CloudFoxable profile
                         │
                         ▼
                    AWS Account
                         │
                         └── Intentionally vulnerable CloudFoxable resources
```

The working setup currently uses:

- **Home lab:** Proxmox
- **Assessment host:** Ubuntu LXC container
- **Cloud tooling:** AWS CLI and Terraform
- **Target environment:** CloudFoxable in AWS

## Evidence Captured So Far

The sanitized setup screenshots are stored in [`media/screenshots`](media/screenshots/).

Suggested highlights:

1. `01-proxmox-create-lxc.png` – Ubuntu LXC creation command in Proxmox
2. `02-install-aws-cli.png` – AWS CLI installation in the lab container
3. `03-install-terraform-repo.png` – HashiCorp repository setup
4. `04-aws-create-user-review.png` – AWS deployer user review page (redacted)
5. `08-terraform-init-success.png` – successful Terraform initialization
6. `09-terraform-plan-summary.png` – Terraform plan summary (redacted)
7. `11-cloudfoxable-deployment-summary.png` – deployment summary and next steps (redacted)
8. `13-ctf-starting-user-verified.png` – AWS STS identity verification for the CTF starting user (redacted)

## Planned Finding Structure

Each finding should follow the same structure:

1. **Title / weakness**
2. **Why it matters**
3. **Initial access / discovery path**
4. **Evidence**
5. **Exploitation or validation steps**
6. **Business impact**
7. **Remediation**
8. **Retest / proof of fix**

## Repository Layout

```text
.
├── README.md
├── docs/
│   ├── assessment-plan.md
│   ├── lab-setup-walkthrough.md
│   ├── professor-proposal-email.md
│   └── report-outline.md
├── findings/
│   ├── 01-finding-template.md
│   ├── 02-finding-template.md
│   ├── 03-finding-template.md
│   └── 04-finding-template.md
├── media/
│   └── screenshots/
├── remediation/
│   └── remediation-log-template.md
└── templates/
    └── finding-template.md
```

## Next Steps

1. Capture the first completed attack path end-to-end.
2. Record the exact commands used for enumeration and validation.
3. Add screenshots before and after remediation.
4. Convert the technical findings into business-facing risk language.
5. Produce the final report and a short project demo.

## Attribution

CloudFoxable is maintained by Bishop Fox. This repository documents **my deployment, testing process, evidence, and analysis**, not the original lab source itself.
