# Lab Setup Walkthrough

## Purpose

This phase establishes a dedicated workstation for authorized CloudFoxable testing and separates the **privileged deployment identity** from the **lower-privilege CTF starting identity** used for assessment work.

## 1. Assessment Workstation

I created an Ubuntu LXC inside my Proxmox home lab and used it as the project security workstation. AWS CLI and Terraform were installed inside the container so the lab could be deployed and tested from an isolated system rather than my primary workstation.

## 2. AWS Deployment Identity

A dedicated IAM user named `CloudFoxableDeployer` was created for provisioning the intentionally vulnerable environment.

Public evidence is sanitized to remove the AWS account identifier.

![Sanitized deployer configuration](../media/screenshots/04-aws-create-user-review.png)

The deployer identity is **not** the identity used to begin the attack-path exercises. Its role is limited to creating and later destroying the CloudFoxable lab.

## 3. CloudFoxable Deployment

CloudFoxable was initialized and deployed with Terraform in the lab AWS account. Terraform created the intentionally vulnerable resources and generated the credentials for the CTF starting user.

Secret-bearing Terraform output, state files, AWS credential files, and environment-specific identifiers are intentionally excluded from this repository.

## 4. Starting Identity

The generated CloudFoxable credentials were written to a separate AWS CLI profile named `cloudfoxable`.

The starting context was then verified with:

```bash
aws sts get-caller-identity --profile cloudfoxable
```

The public screenshot below has the AWS account number and unique user identifier redacted while retaining the identity name needed to demonstrate the testing context.

![Sanitized STS verification](../media/screenshots/13-ctf-starting-user-verified.png)

The result confirms that subsequent enumeration begins as:

```text
user/ctf-starting-user
```

## 5. Separation of Duties

The project intentionally maintains two different contexts:

| Identity | Purpose |
| --- | --- |
| `CloudFoxableDeployer` | Provision and destroy the training environment |
| `ctf-starting-user` | Begin enumeration and controlled attack-path testing |

Keeping those roles separate makes the technical walkthrough clearer and avoids presenting administrator access as the starting point of the assessment.

## Next Phase

The next stage is AWS enumeration from the CTF starting identity, followed by documentation of discovered attack paths, controlled exploitation, remediation, and retesting.
