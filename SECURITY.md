# Security Policy

## Purpose

This document defines how security issues affecting `dodger` must be
reported, handled, remediated, and disclosed. The goal is to ensure that
security-relevant findings are managed confidentially, triaged consistently,
and resolved within appropriate operational timelines.

## Supported Versions

Security fixes are provided for supported releases only, beginning with the first production release v1.0.0

| Version | Supported |
| ------- | --------- |
| `main` / latest release | Yes |
| Previous minor release | Yes |
| Older releases | No |

## Confidential Reporting

Security issues must be reported through confidential channels only. Public
GitHub issues, public pull requests, or other public forums must not be used
for reporting vulnerabilities.

Approved reporting channels:

- GitHub Private Vulnerability Reporting / Security Advisories
- Email: `stefan.machmeier@uni-heidelberg.de`

Reports should include, where available:

- A concise description of the issue
- Affected component, endpoint, container, or workflow
- Reproduction steps or validation details
- Expected impact and potential exploitation scenario
- Affected version, branch, commit, or image tag
- Relevant logs, screenshots, request samples, or proof-of-concept material
- Whether the issue appears actively exploited or time-sensitive

## Confidentiality Requirements

All reported security issues are handled as confidential until review is
complete and a coordinated disclosure decision has been made.

During this period:

- Issue details must not be disclosed publicly
- Sensitive technical details must be shared only on a need-to-know basis
- Access to internal discussion, remediation branches, and advisory drafts
  should be restricted
- If there is evidence of active exploitation, internal escalation should occur
  immediately

## Intake and Triage

Each report is reviewed to determine:

- Whether the issue is reproducible
- Whether it affects a supported version
- Whether there is a meaningful confidentiality, integrity, or availability impact
- Whether exploitation requires special conditions or privileged access
- Whether the issue represents active exploitation, a misconfiguration, or a
  theoretical weakness without practical impact

Severity should be classified as `Critical / High / Medium / Low`.

## Response Targets

The following target times apply to supported versions and valid security
reports. These targets are operational goals, not contractual guarantees.

| Stage | Target |
| ----- | ------ |
| Initial acknowledgement | Within 2 business days |
| Initial triage decision | Within 5 business days |
| First remediation update | Within 7 calendar days |
| Ongoing status updates | At least every 7 calendar days |
| Critical issue remediation plan | Within 7 calendar days |
| High severity remediation plan | Within 14 calendar days |
| Medium severity remediation plan | Within 30 calendar days |
| Low severity remediation plan | Best effort |

If a report indicates active exploitation, credential exposure, remote code
execution, or broad unauthorized access, the issue should be escalated as an
incident and handled with priority outside normal backlog processes.

## Remediation Process

When a security issue is confirmed, maintainers should:

- Reproduce and validate the issue
- Define affected versions and deployment scenarios
- Prepare a remediation plan proportional to the severity
- Implement and review the fix
- Backport the fix to supported versions where feasible
- Validate the fix before release
- Prepare customer-facing or operator-facing guidance if configuration or
  operational action is required

Where immediate remediation is not possible, temporary mitigations should be
documented and communicated clearly.

## Disclosure and Publication

Confirmed vulnerabilities are disclosed in a coordinated manner after one of
the following conditions is met:

- A fix has been released
- A mitigation has been published and the residual risk is understood
- A disclosure deadline has been reached and leadership approves publication

The default disclosure target is `90 days`, but the actual window may be
shortened or extended based on:

- Evidence of exploitation
- Fix availability and deployment risk
- Customer exposure
- Dependency or vendor coordination needs

Public disclosures may include:

- A security advisory
- Release notes
- Upgrade or mitigation instructions
- Severity and affected-version information

## Operational Communication

Where a confirmed issue affects deployed environments, communication should be
proportionate to impact. This may include:

- Internal security or operations escalation
- Notification to administrators, customers, or service owners
- Temporary mitigation guidance
- Required upgrade or rotation steps
- Post-remediation confirmation and closure

Security communications should avoid unnecessary disclosure of exploit details
before mitigations are available.

## Scope

The following areas are considered in scope for security handling:

- Authentication and authorization controls
- Password handling and account lifecycle
- File upload, parsing, and processing pipelines
- Secrets handling and environment configuration
- Data access controls and audit logging
- Container, service, and network configuration
- Dependency vulnerabilities with validated product impact
- Sensitive data exposure, privilege escalation, SSRF, RCE, injection, and
  broken access control

## Out of Scope

The following are generally not treated as security vulnerabilities unless
clear and demonstrated security impact exists:

- Cosmetic misconfigurations without exploitability
- Missing hardening headers without a practical attack path
- Issues affecting unsupported or end-of-life releases only
- Hypothetical findings without reproducible impact
- Third-party platform issues outside the control of this project
- Reports based only on scanner output without technical validation

## Safe Handling Expectations

Anyone validating a suspected issue is expected to act in a controlled and
minimal manner.

Expected behavior:

- Limit activity to what is necessary to confirm the issue
- Avoid unauthorized access to non-public or third-party data
- Avoid disruption of production systems
- Avoid persistence, data modification, or data destruction
- Stop testing and report promptly once the issue is confirmed

This policy does not authorize:

- Access to data belonging to other users or organizations
- Service disruption or denial-of-service activity
- Data exfiltration or retention of sensitive information
- Any activity that violates applicable law or contractual obligations

## Security Updates

Security fixes may be distributed through one or more of the following:

- Normal release process
- Out-of-band patch release
- Security advisory
- Operational mitigation notice

Where appropriate, the published update should include:

- Affected versions
- Fixed versions
- Severity
- Upgrade path
- Required operational actions

## Escalation

If no acknowledgement is received within the response target above, the report
should be resent to:

- `stefan.machmeier@uni-heidelberg.de`

Urgent reports involving active exploitation or high-confidence compromise
should use the subject line:

`[URGENT SECURITY REPORT]`

## Policy Maintenance

This policy should be reviewed whenever:

- Reporting channels change
- Supported versions change
- Incident response expectations change
- Disclosure commitments change

Last reviewed: `11-04-2026`
