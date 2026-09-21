# Assessment Plan

## Goal
Perform a hands-on AWS security assessment against an intentionally vulnerable training environment and translate the results into a business-focused report.

## Objectives
- identify at least four weaknesses or attack paths
- validate each issue in the lab
- document evidence and likely impact
- remediate the root cause
- retest and confirm the issue is fixed

## Working Methodology
1. **Lab setup** – build the assessment environment and deploy CloudFoxable.
2. **Enumeration** – inspect IAM, accessible services, secrets exposure, and privilege paths.
3. **Validation** – confirm the finding with controlled testing in the isolated lab.
4. **Documentation** – capture commands, screenshots, short terminal recordings, and findings notes.
5. **Remediation** – apply the fix and record what changed.
6. **Retesting** – prove the original path no longer works.

## Expected Deliverables
- GitHub repository with technical evidence that excludes credentials and secret-bearing artifacts
- technical write-up for each finding
- business-facing final report
- short demo videos for selected assessment phases and findings
