# Portfolio Evidence Guide

This repository is designed as a public, sanitized engineering case study. The original internship material contains strong visual evidence, but several captures also expose environment-specific infrastructure details that should not be published without redaction.

## Reviewed Visual Evidence

The following screenshots are especially useful for the portfolio because they demonstrate both system operation and analyst workflow.

| Evidence | What it demonstrates | Recommended use | Publication status |
|---|---|---|---|
| Wazuh Overview dashboard | Active agents, alert severity distribution, and available security modules | README / portfolio hero evidence | Strong; review identifiers before upload |
| Discover view using `wazuh-alerts-*` | Indexed events can be filtered and queried | Core implementation evidence | Redact IP addresses |
| GeoIP map visualization | Geographic enrichment using `GeoLocation.location` | GeoIP lab evidence | Strong; publish only after reviewing plotted data |
| GeoIP layer configuration | How the map layer is connected to Wazuh alert data | Technical lab evidence | Generally safe after identifier review |
| MITRE ATT&CK dashboard | Alerts organized into ATT&CK-oriented tactics and views | Core analysis evidence | Redact internal URL, endpoint/agent name, and browser context |
| Vulnerability Detection dashboard | CVE-oriented security visibility and severity review | Core implementation evidence | Prefer a populated dashboard over an empty visualization |
| Security activity summary | Quantitative evidence of monitoring workload | README / analysis evidence | Strong after sanitization |
| Top alert categories | Types of rule-triggered events reviewed | Analysis evidence | Strong after sanitization |
| FIM endpoint activity | File-integrity telemetry and change concentration | FIM evidence | Redact endpoint names and IP addresses |
| Graylog dashboard | Centralized log visualization beyond the default Wazuh UI | Integration evidence | Redact hostnames/IPs |
| MISP events dashboard | Threat-intelligence workflow evidence | Integration evidence | Redact internal event/context identifiers if present |
| Email alert example | Operational notification flow | Alerting evidence | Redact email addresses and message-specific identifiers |

## Dashboard Snapshot Observed in the Evidence

One Wazuh Overview screenshot shows:

- **9 active agents**,
- **3 critical-severity alerts**,
- **1 high-severity alert**,
- **1,825 medium-severity alerts**,
- **60,940 low-severity alerts**

for the displayed 24-hour window.

This snapshot is useful as visual evidence that the environment was actively collecting and classifying events. It should be presented as a point-in-time dashboard view, not as a project-wide total.

The same dashboard exposes modules including File Integrity Monitoring, Configuration Assessment, Malware Detection, Threat Hunting, Vulnerability Detection, MITRE ATT&CK, Docker monitoring, and compliance-related views.

## MITRE ATT&CK Evidence

The reviewed ATT&CK dashboard displays tactics including:

- Credential Access,
- Initial Access,
- Privilege Escalation,
- Defense Evasion,
- Persistence,
- Lateral Movement.

The internship notes also discuss Discovery, Reconnaissance, and Impact in the ATT&CK analysis context.

Use [`docs/mitre-attack.md`](docs/mitre-attack.md) for the portfolio explanation. Do **not** describe these mapped alerts as proof that every tactic was successfully executed by an attacker.

## Vulnerability Evidence

The internship documentation includes a populated Vulnerability Detection dashboard showing a point-in-time severity breakdown of:

- 3 critical,
- 13 high,
- 16 medium,
- 2 low,
- 45 pending evaluation.

This is stronger portfolio evidence than an empty or `No results found` visualization because it demonstrates that vulnerability data was actually available for review.

## GeoIP Evidence

The reviewed Maps configuration uses:

```text
Index pattern: wazuh-alerts-*
Geospatial field: GeoLocation.location
```

A separate screenshot shows a plotted event in the East Java area. This is useful evidence for the GeoIP enrichment lab, but the map should be framed as event geolocation context rather than proof of a person's physical location.

## Recommended Screenshot Layout

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

## Suggested Captions

### Wazuh Overview

> **Wazuh Overview dashboard.** A point-in-time view showing monitored agents, alert severity distribution, and access to endpoint-security, threat-intelligence, compliance, and container-monitoring modules.

### Discover

> **Indexed security events.** The `wazuh-alerts-*` index was queried in Discover to validate that endpoint events were ingested and searchable by fields such as agent metadata.

### GeoIP

> **GeoIP-enriched event visualization.** Wazuh alert data was visualized using the `GeoLocation.location` field to provide geographic context during investigation.

### MITRE ATT&CK

> **MITRE ATT&CK dashboard.** Alert mappings were reviewed through ATT&CK-oriented views such as top tactics, alert evolution, and rule-level distributions. These mappings provide investigation context rather than automatic confirmation of compromise.

### Vulnerability Detection

> **Vulnerability Detection dashboard.** A point-in-time view of CVE-related findings grouped by severity to support prioritization and remediation review.

## Mandatory Redaction Checklist

Before publishing any screenshot, check for:

- internal IPv4/IPv6 addresses,
- public server addresses that identify organizational infrastructure,
- internal hostnames and DNS names,
- endpoint/agent names tied to the organization,
- dashboard URLs exposing private addressing,
- email addresses,
- student/employee identifiers,
- usernames where they reveal real infrastructure context,
- API keys, passwords, tokens, cookies, session values, or SMTP credentials,
- organization-specific paths or URLs that should remain private,
- raw logs containing user or system-identifying data,
- unrelated browser tabs exposing internal systems.

Replace environment-specific labels with generic values where useful:

```text
01-Wazuh              -> siem-manager
<real-hostname>       -> web-server-01
<internal-ip>         -> 10.x.x.x
<public-server-ip>    -> <PUBLIC_SERVER_IP>
<real-email>          -> security@example.org
```

## Important: Do Not Publish Raw Working Configurations

Some original internship notes contain environment-specific configuration values. Public portfolio files should use placeholders such as:

```text
<PASSWORD>
<API_KEY>
<INTERNAL_IP>
<MANAGER_HOST>
```

Do not copy raw Docker Compose, SMTP, Graylog, OpenSearch, MaxMind, VirusTotal, or other credential-bearing configurations into the public repository without sanitizing them first.

## What Counts as Strong Evidence?

A good portfolio screenshot should answer at least one of these questions:

1. **What did the system look like?** — architecture or dashboard.
2. **What did you configure?** — sanitized configuration or integration view.
3. **What did the system detect?** — alert/event analysis.
4. **What did you conclude?** — chart, table, or short analyst note.

Screenshots are most useful when paired with a short explanation. Avoid publishing a dashboard image without explaining what the reader should learn from it.

## Evidence Integrity

Do not create fake screenshots or alter monitoring values to make the project appear larger. Redaction is acceptable; changing the meaning of the evidence is not.

The public repository should preserve a clear distinction between:

- **final implementation evidence**, supported by the internship report,
- **lab / explored integrations**, supported by working notes,
- **future improvements**, which are proposals rather than completed work.
