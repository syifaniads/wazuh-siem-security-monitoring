# Portfolio Evidence Guide

This repository is designed as a public, sanitized engineering case study. The original internship report contains useful visual evidence, but it also includes infrastructure details that should not be published without redaction.

## Recommended Visual Evidence

The strongest screenshots to add later are:

| Evidence | Why it matters | Suggested source |
|---|---|---|
| SIEM architecture | Shows how endpoints, Wazuh, log management, threat intelligence, and alerting fit together | Architecture figure from the implementation section |
| Graylog dashboard | Demonstrates centralized log visualization beyond the default Wazuh interface | `Dashboard Log Graylog` figure |
| MISP events dashboard | Demonstrates the threat-intelligence integration workflow | `Dashboard Events MISP` figure |
| Email alert example | Demonstrates an operational notification path | `Implementasi Notifikasi Alert melalui Email` figure |
| Security activity summary | Gives quantitative evidence of the monitoring workload | `Ringkasan Aktivitas Keamanan` figure |
| Top alert categories | Shows the types of rule-triggered events investigated | `Top 10 Alert Keamanan yang Terdeteksi` figure |
| FIM endpoint activity | Demonstrates analysis of file-integrity telemetry | `Endpoint dengan Aktivitas FIM Tertinggi` figure |
| Malware/rootkit activity | Demonstrates analysis of higher-risk security categories | `Aktivitas Malware dan Rootkit` figure |

## Recommended Screenshot Layout

When screenshots are available, use a structure such as:

```text
screenshots/
├── architecture/
│   └── siem-architecture-sanitized.png
├── wazuh/
│   ├── security-activity-summary.png
│   ├── top-alerts.png
│   └── fim-analysis.png
├── graylog/
│   └── dashboard-sanitized.png
├── misp/
│   └── events-sanitized.png
└── alerting/
    └── email-alert-sanitized.png
```

## Mandatory Redaction Checklist

Before publishing a screenshot, check for:

- internal IPv4/IPv6 addresses,
- public server addresses that identify organizational infrastructure,
- internal hostnames and DNS names,
- endpoint/agent names tied to the organization,
- email addresses,
- student/employee identifiers,
- usernames where they reveal real infrastructure context,
- API keys, passwords, tokens, cookies, session values, or SMTP credentials,
- organization-specific paths or URLs that should remain private,
- raw logs containing user or system-identifying data.

Replace environment-specific labels with generic values where useful, for example:

```text
01-Wazuh              -> siem-manager
<real-hostname>       -> web-server-01
<internal-ip>         -> 10.x.x.x
<public-server-ip>    -> <PUBLIC_SERVER_IP>
<real-email>          -> security@example.org
```

## What Counts as Strong Evidence?

A good portfolio screenshot should answer at least one of these questions:

1. **What did the system look like?** — architecture or dashboard.
2. **What did you configure?** — sanitized configuration or integration view.
3. **What did the system detect?** — alert/event analysis.
4. **What did you conclude?** — chart, table, or short analyst note.

Screenshots are most useful when paired with a short explanation. Avoid publishing a dashboard image without explaining what the reader should learn from it.

## Example Caption

> **File Integrity Monitoring analysis.** The monitoring period showed concentrated FIM activity on a small number of endpoints. These events were reviewed as change indicators rather than automatically classified as malicious activity.

## Evidence Integrity

Do not create fake screenshots or alter monitoring values to make the project appear larger. Redaction is acceptable; changing the meaning of the evidence is not.

The public repository should preserve a clear distinction between:

- **final implementation evidence**, supported by the internship report,
- **lab / explored integrations**, supported by working notes,
- **future improvements**, which are proposals rather than completed work.
