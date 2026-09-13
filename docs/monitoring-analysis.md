# Monitoring & Security Analysis

## Monitoring snapshot

The documented monitoring period recorded **663,762 security alerts**. Authentication activity was a major contributor, with **37,433 successful logins** and **2,852 failed logins**.

The exported Wazuh reports also showed a small number of higher-severity events, including six alerts at level 12 or above during the summarized monitoring window.

## Examples of observed alert categories

The monitoring reports included rule matches associated with:

- Windows logon success and logoff events
- failed authentication and multiple logon failures
- web server HTTP 400 responses
- CMS login attempts and brute-force indicators
- SQL injection attempt alerts
- Shellshock-related alerts
- file and registry integrity changes
- host-based anomaly / rootcheck events
- possible kernel-level rootkit alerts
- agent disconnect and queue-capacity events

## Interpreting the data

A SIEM alert is not equivalent to a confirmed compromise.

For example:

- a file-integrity alert can be caused by a legitimate package upgrade
- repeated authentication failures can be user error, automation, or malicious probing
- an SQL-injection rule match requires request and application context before it can be classified as an actual exploitation attempt
- rootcheck findings require validation to distinguish suspicious artifacts from false positives or expected system behavior

The monitoring workflow therefore focuses on **triage and contextual investigation**, rather than treating every rule match as an incident.

## MITRE ATT&CK mapping

Selected activities were mapped to MITRE ATT&CK categories in the internship analysis. Examples included:

| Observed activity | Security interpretation used in analysis |
|---|---|
| Login failure | Brute-force related activity |
| Multiple login failure | Credential-access related activity |
| SQL injection alert | Initial-access related activity |
| Privilege assignment | Privilege-escalation related activity |
| Rootkit detection | Persistence / defense-evasion related activity |

These mappings are useful for organizing security telemetry, but the technique classification still depends on event context.

## Compliance-oriented reporting

The Wazuh environment generated security-control mappings and reports for frameworks or standards such as:

- PCI DSS
- GDPR
- HIPAA
- Trust Services Criteria (TSC)
- NIST SP 800-53

These reports should be understood as **monitoring/control mappings generated from rules**, not as evidence that the organization is automatically certified or fully compliant with those standards.

## Key lessons

1. Large alert volumes make prioritization and tuning essential.
2. Authentication events dominate many environments and require baselining.
3. FIM is valuable only when routine changes can be distinguished from suspicious changes.
4. Severity alone is not enough; investigation needs asset, user, source, and timing context.
5. Threat-intelligence and MITRE mappings improve investigation structure, but do not replace validation.
