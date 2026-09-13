# Screenshot Evidence

This directory contains the **sanitized visual evidence** intentionally published with the portfolio case study.

Only two screenshots are included publicly. This is deliberate: the goal is to provide strong, readable evidence without exposing unnecessary infrastructure details or flooding the repository with setup screenshots.

## Published Evidence

### 1. Wazuh Overview Dashboard

File: [`wazuh-overview-dashboard-sanitized.png`](wazuh-overview-dashboard-sanitized.png)

![Wazuh Overview Dashboard](wazuh-overview-dashboard-sanitized.png)

**What it demonstrates**

- the Wazuh monitoring environment was active,
- multiple agents were being monitored,
- alerts were classified by severity,
- endpoint-security and threat-intelligence modules were available from the dashboard.

**Suggested caption**

> **Wazuh Overview dashboard.** Point-in-time evidence of monitored agents, alert severity distribution, and the available endpoint-security and threat-intelligence capabilities.

---

### 2. MITRE ATT&CK Dashboard

File: [`wazuh-mitre-attack-dashboard-sanitized.png`](wazuh-mitre-attack-dashboard-sanitized.png)

![Wazuh MITRE ATT&CK Dashboard](wazuh-mitre-attack-dashboard-sanitized.png)

**What it demonstrates**

- Wazuh alerts were reviewed through ATT&CK-oriented views,
- the dashboard included top tactics, alert evolution, rule level by attack, and rule level by tactic,
- selected rule matches were mapped into adversary-behavior context for investigation.

**Suggested caption**

> **MITRE ATT&CK dashboard.** Wazuh rule matches reviewed through ATT&CK-oriented views such as top tactics, alert evolution, and rule-level distributions. The mappings provide analyst context and do not by themselves confirm compromise.

## Why Other Screenshots Are Not Published

The internship material contains additional dashboards and configuration captures for areas such as vulnerability detection, GeoIP mapping, Graylog, MISP, email alerting, File Integrity Monitoring, and security-activity summaries. Some of those captures expose environment-specific identifiers, infrastructure details, or add little value beyond the two screenshots already published.

Their findings are documented in text form elsewhere in the repository instead of publishing raw screenshots.

See:

- [`../EVIDENCE.md`](../EVIDENCE.md)
- [`../docs/vulnerability-detection.md`](../docs/vulnerability-detection.md)
- [`../docs/mitre-attack.md`](../docs/mitre-attack.md)
- [`../labs/geoip-enrichment.md`](../labs/geoip-enrichment.md)

## Redaction Standard

Before any future screenshot is added, review it for:

- internal or public infrastructure IP addresses,
- internal URLs and hostnames,
- endpoint or agent names tied to the organization,
- email addresses and user identifiers,
- credentials, API keys, tokens, cookies, or session values,
- unrelated browser tabs exposing internal systems,
- raw log data that identifies systems or users.

Redaction may hide sensitive identifiers, but it must **not change alert counts, chart values, or the meaning of the evidence**.
