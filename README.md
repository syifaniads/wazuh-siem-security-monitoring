# Wazuh SIEM Security Monitoring

A sanitized engineering case study based on my internship work implementing and evaluating a centralized security monitoring environment using **Wazuh**, with supporting integrations for **Graylog**, **MISP**, and email alerting.

> This repository intentionally excludes credentials, private infrastructure details, internal hostnames, internal IP addresses, and other sensitive organizational information. Example configurations use placeholders and generic identifiers.

## Project Summary

The project focused on improving visibility into endpoint and server security events through centralized collection, detection, analysis, and reporting.

Core capabilities documented in the final implementation include:

- Wazuh-based SIEM monitoring
- Endpoint agent enrollment and centralized event collection
- File Integrity Monitoring (FIM)
- Vulnerability detection
- Security log analysis and alert review
- Graylog integration for centralized log visualization and analysis
- MISP integration for threat-intelligence workflows
- Email alert notification
- MITRE ATT&CK mapping for selected security activities
- Security and compliance-oriented reporting

## Architecture

```mermaid
flowchart TD
    A[Linux / Windows Endpoints] -->|Wazuh Agent| B[Wazuh Manager]
    B --> C[Wazuh Indexer]
    C --> D[Wazuh Dashboard]
    B --> E[Graylog]
    B --> F[MISP / Threat Intelligence]
    B --> G[Email Alerting]
    B --> H[Detection & Analysis]
    H --> H1[Authentication Events]
    H --> H2[File Integrity Monitoring]
    H --> H3[Vulnerability Events]
    H --> H4[Web Security Alerts]
```

See [`architecture/architecture.md`](architecture/architecture.md) for the design rationale and data flow.

## What I Worked On

- Configured and operated a Wazuh-based centralized monitoring environment.
- Enrolled endpoints and validated event delivery to the manager.
- Configured File Integrity Monitoring to detect changes to monitored system and application files.
- Enabled vulnerability detection using endpoint inventory data.
- Reviewed authentication, file integrity, malware/rootkit, and web-related security alerts.
- Integrated Wazuh-generated data with Graylog for additional log management and visualization.
- Used MISP as part of the threat-intelligence workflow.
- Configured email-based alert notifications.
- Mapped selected alert categories to MITRE ATT&CK tactics/techniques.
- Reviewed Wazuh-generated compliance-oriented reports including PCI DSS, GDPR, HIPAA, TSC, and NIST 800-53 mappings.

## Monitoring Snapshot

One documented monitoring window contained:

| Metric | Observed value |
|---|---:|
| Total security alerts | 663,762 |
| Authentication successes | 37,433 |
| Authentication failures | 2,852 |
| Alerts at level 12 or above | 6 |

Examples of rule-triggered activity included:

- multiple authentication failures
- CMS login attempts and brute-force indicators
- web server error patterns
- SQL injection attempt alerts
- Shellshock-related alerts
- file and registry integrity changes
- rootcheck / possible rootkit alerts
- Wazuh agent queue and connectivity events

**Important:** these are SIEM rule matches and monitoring observations, not automatically confirmed security incidents. Alert context must be investigated before classifying an event as malicious.

## Repository Structure

```text
.
├── README.md
├── DISCLAIMER.md
├── SECURITY.md
├── architecture/
│   └── architecture.md
├── docs/
│   ├── implementation-overview.md
│   ├── file-integrity-monitoring.md
│   ├── vulnerability-detection.md
│   ├── graylog-integration.md
│   ├── misp-integration.md
│   └── monitoring-analysis.md
├── labs/
│   └── README.md
├── configs/
│   └── wazuh/
│       ├── fim-example.xml
│       ├── vulnerability-detection.xml
│       └── alerting-example.xml
└── reports/
    └── README.md
```

## Core Documentation

- [Implementation overview](docs/implementation-overview.md)
- [Architecture](architecture/architecture.md)
- [File Integrity Monitoring](docs/file-integrity-monitoring.md)
- [Vulnerability Detection](docs/vulnerability-detection.md)
- [Graylog Integration](docs/graylog-integration.md)
- [MISP Integration](docs/misp-integration.md)
- [Monitoring & Security Analysis](docs/monitoring-analysis.md)

## Additional Labs

My internship notes also covered additional security integrations and experiments such as Suricata, ClamAV, Security Configuration Assessment, Docker monitoring, GeoIP enrichment, Active Response, VirusTotal, archive management, and index lifecycle management.

These are separated under [`labs/`](labs/README.md) because the available final report does not establish every item as part of the final deployed production monitoring stack.

## Security & Privacy

This repository is a **sanitized portfolio reconstruction**. It does not publish raw production logs, credentials, organization-specific endpoint names, private infrastructure addresses, or confidential operational details.

Read [`SECURITY.md`](SECURITY.md) and [`DISCLAIMER.md`](DISCLAIMER.md) before reusing any configuration examples.

## Portfolio Description

> Implemented a centralized security monitoring environment using Wazuh with Graylog and MISP integrations. Configured file integrity monitoring, vulnerability detection, log analysis, and alerting, and analyzed more than 663K security events while mapping selected activities to MITRE ATT&CK.
