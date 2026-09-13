# Screenshot Evidence

This directory is reserved for **sanitized visual evidence** from the internship project.

Do not upload raw production captures without reviewing them first. Several original screenshots contain private infrastructure addresses, endpoint names, or browser URLs.

## Recommended Structure

```text
screenshots/
├── architecture/
│   └── siem-architecture-sanitized.png
├── wazuh/
│   ├── overview-dashboard-sanitized.png
│   ├── discover-events-sanitized.png
│   ├── mitre-attack-dashboard-sanitized.png
│   ├── vulnerability-dashboard-sanitized.png
│   ├── security-activity-summary.png
│   ├── top-alerts.png
│   └── fim-analysis.png
├── geoip/
│   ├── map-sanitized.png
│   └── layer-configuration-sanitized.png
├── graylog/
│   └── dashboard-sanitized.png
├── misp/
│   └── events-sanitized.png
└── alerting/
    └── email-alert-sanitized.png
```

## Priority Evidence

### 1. Wazuh Overview Dashboard

Use as a high-level proof that the monitoring environment was active.

Suggested caption:

> **Wazuh Overview dashboard.** Point-in-time evidence of monitored agents, alert severity distribution, and available endpoint-security, threat-intelligence, compliance, and container-monitoring modules.

### 2. MITRE ATT&CK Dashboard

Use to support [`../docs/mitre-attack.md`](../docs/mitre-attack.md).

Suggested caption:

> **MITRE ATT&CK dashboard.** Wazuh alerts reviewed through ATT&CK-oriented views such as top tactics, alert evolution, and rule-level distributions. ATT&CK mappings provide analyst context and do not by themselves confirm compromise.

### 3. GeoIP Map

Use to support [`../labs/geoip-enrichment.md`](../labs/geoip-enrichment.md).

Suggested caption:

> **GeoIP-enriched event visualization.** Alert data from `wazuh-alerts-*` was plotted using `GeoLocation.location` to provide geographic context during investigation.

### 4. Discover View

Suggested caption:

> **Indexed Wazuh events.** The `wazuh-alerts-*` index was queried in Discover to validate that endpoint events were successfully ingested and searchable.

### 5. Vulnerability Detection

Prefer the populated vulnerability dashboard from the internship documentation rather than an empty pie chart or `No results found` view.

Suggested caption:

> **Vulnerability Detection dashboard.** Point-in-time CVE findings grouped by severity to support vulnerability prioritization and remediation review.

## Redaction Rules

Before publishing an image, redact:

- internal IP addresses,
- public infrastructure IPs when they identify the environment,
- hostnames and endpoint names,
- private dashboard URLs,
- agent identifiers when they expose infrastructure context,
- email addresses,
- credentials, API keys, session values, or tokens,
- unrelated browser tabs that reveal internal systems.

Do not change chart values, alert counts, or other evidence merely to make the project appear stronger.

See [`../EVIDENCE.md`](../EVIDENCE.md) for the full evidence guide and redaction checklist.
