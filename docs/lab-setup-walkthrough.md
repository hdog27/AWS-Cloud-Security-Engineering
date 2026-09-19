# Lab Setup Walkthrough

This file documents the initial setup evidence captured so far.

## 1. Build the Ubuntu lab container
- `media/screenshots/01-proxmox-create-lxc.png`

## 2. Install AWS CLI in the container
- `media/screenshots/02-install-aws-cli.png`
- `media/screenshots/06-aws-cli-installed-login-attempt.png`

## 3. Configure Terraform tooling
- `media/screenshots/03-install-terraform-repo.png`
- `media/screenshots/08-terraform-init-success.png`

## 4. Create the AWS deployer user
- `media/screenshots/04-aws-create-user-review.png`
- `media/screenshots/12-aws-retrieve-password.png`

## 5. Deploy CloudFoxable
- `media/screenshots/09-terraform-plan-summary.png`
- `media/screenshots/11-cloudfoxable-deployment-summary.png`
- `media/screenshots/10-cloudfoxable-next-steps.png`

## Notes
- Account identifiers were redacted before saving these images for portfolio use.
- Images were re-saved locally with metadata stripped.
- Some screenshots are duplicates or alternate crops and can be removed later if the repo becomes too cluttered.

## 6. Verify the CloudFoxable starting identity
- `media/screenshots/13-ctf-starting-user-verified.png` – `aws sts get-caller-identity` confirms the assessment profile is operating as the CloudFoxable CTF starting user.
