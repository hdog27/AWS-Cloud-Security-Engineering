# AWS Environment Enumeration

## Purpose

Before validating individual CloudFoxable attack paths, I performed a reconnaissance pass from the intentionally limited `ctf-starting-user` identity.

The goal was to answer the same questions I would ask at the start of a cloud security assessment:

- Who am I authenticated as?
- What AWS services and resources can this identity see?
- Are any public-facing endpoints exposed?
- Are EC2 instances visible?
- Which IAM users and roles can be enumerated?

This phase is reconnaissance, not exploitation. The results are used to select resources and permissions for deeper validation.

## Starting Identity

The assessment begins by verifying the active AWS identity:

```bash
aws sts get-caller-identity --profile cloudfoxable
```

The active profile resolves to CloudFoxable's intended `ctf-starting-user`, keeping the assessment separate from the deployment identity used to build the lab.

## CloudFox Enumeration

### Resource Inventory

```bash
cloudfox aws --profile cloudfoxable -v2 inventory
```

The inventory pass identifies AWS services and resources visible to the current identity. It provides a high-level map of the environment and highlights services worth investigating further.

### Endpoint Discovery

```bash
cloudfox aws --profile cloudfoxable -v2 endpoints
```

This command enumerates service endpoints visible to the current identity. During the lab assessment, the results exposed public Lambda Function URLs that became candidates for later application testing.

### EC2 Enumeration

```bash
cloudfox aws --profile cloudfoxable -v2 instances
```

The instance enumeration checks for visible EC2 workloads and associated addressing or instance-role information. No EC2 instances were identified during this initial pass.

### IAM Principal Enumeration

```bash
cloudfox aws --profile cloudfoxable -v2 principals
```

The principals command enumerates visible IAM users and roles. This provides context for later IAM permission analysis, role trust review, and privilege-path investigation.

## What This Demonstrates

Cloud reconnaissance is different from a traditional network scan. Instead of discovering only hosts and open ports, cloud assessment tools can query the provider control plane for resources, identities, configuration, and service endpoints that the current principal is authorized to view.

A constrained identity can therefore reveal useful attack-surface information without possessing administrator access. The amount of information returned depends on the IAM permissions assigned to that identity.

## Recorded Demo

The edited terminal recording for this phase is stored at:

`media/videos/01-cloudfoxable-enumeration.mp4`

The recording shows the identity check followed by the inventory, endpoint, EC2, and IAM principal enumeration commands.

## Next Step

The enumeration results are used to choose specific CloudFoxable attack paths for controlled validation. Public Lambda Function URLs discovered during this phase were the first resources selected for deeper testing.
