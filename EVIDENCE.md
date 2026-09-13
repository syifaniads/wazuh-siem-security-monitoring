# Portfolio Evidence Guide

This repository is a **public, sanitized engineering case study**. The original internship material contains more screenshots and implementation details than are published here, but several captures expose environment-specific infrastructure information.

For the public portfolio, the evidence set is intentionally small and focused.

## Published Visual Evidence

Two sanitized screenshots are included in [`screenshots/`](screenshots/README.md):

| Evidence | File | What it demonstrates |
|---|---|---|
| Wazuh Overview dashboard | [`wazuh-overview-dashboard-sanitized.png`](screenshots/wazuh-overview-dashboard-sanitized.png) | Active monitoring, agent visibility, severity distribution, and available security modules |
| MITRE ATT&CK dashboard | [`wazuh-mitre-attack-dashboard-sanitized.png`](screenshots/wazuh-mitre-attack-dashboard-sanitized.png) | ATT&CK-oriented investigation views such as top tactics, alert evolution, and rule-level distributions |

These two screenshots are the primary visual evidence used by the repository and are embedded directly in the main [`README.md`](README.md).

## Wazuh Overview Snapshot

One Wazuh Overview screenshot shows the following point-in-time state:

- **9 active agents**,
- **3 critical-severity alerts**,
- **1 high-severity alert**,
- **1,825 medium-severity alerts**,
- **60,940 low-severity alerts**

for the displayed 24-hour window.

The same dashboard exposes modules including File Integrity Monitoring, Configuration Assessment, Malware Detection, Threat Hunting, Vulnerability Detection, MITRE ATT&CK, Docker monitoring, and compliance-oriented views.

This is a **snapshot**, not a project-wide alert total.

## MITRE ATT&CK Evidence

The published ATT&CK dashboard contains tactics including:

- Credential Access,
- Initial Access,
- Privilege Escalation,
- Defense Evasion,
- Persistence,
- Lateral Movement.

The internship working notes also discuss Discovery, Reconnaissance, and Impact in the ATT&CK analysis context.

The dashboard should be interpreted as **rule-to-ATT&CK mapping for investigation context**. A mapped alert is not automatic proof that an attacker successfully completed the mapped tactic.

See [`docs/mitre-attack.md`](docs/mitre-attack.md).

## Additional Evidence Supported by the Internship Material

The original material also contains evidence for the following areas, but the corresponding screenshots are **not currently published** in the public repository:

| Area | Supported observation | Public treatment |
|---|---|---|
| Vulnerability Detection | Populated dashboard with severity-based CVE findings | Findings summarized in text only |
| GeoIP / Maps | `wazuh-alerts-*` mapped through `GeoLocation.location` | Configuration and validation summarized in the GeoIP lab |
| Discover | Wazuh alert events were queryable and filterable | Described in documentation; raw IP-bearing screenshot omitted |
| Graylog | Additional log-management and visualization workflow | Documented in `docs/graylog-integration.md` |
| MISP | Threat-intelligence workflow | Documented in `docs/misp-integration.md` |
| Email alerting | Operational notification path | Sanitized configuration example only |
| File Integrity Monitoring | Endpoint file-change monitoring | Documented in `docs/file-integrity-monitoring.md` |
| Security activity summary | Quantitative monitoring results | Summarized in `docs/monitoring-analysis.md` |

Not publishing every available screenshot is intentional. A smaller evidence set reduces accidental disclosure and keeps the case study focused.

## Vulnerability Snapshot

The internship documentation includes a populated Vulnerability Detection dashboard showing a point-in-time severity breakdown of:

| Severity / State | Count |
|---|---:|
| Critical | 3 |
| High | 13 |
| Medium | 16 |
| Low | 2 |
| Pending evaluation | 45 |

These values are preserved in [`docs/vulnerability-detection.md`](docs/vulnerability-detection.md) without publishing the original asset-specific dashboard capture.

## GeoIP Evidence

The reviewed Wazuh Maps configuration used:

```text
Index pattern: wazuh-alerts-*
Geospatial field: GeoLocation.location
```

A separate working screenshot showed an enriched event plotted in the East Java area. This supports the lab documentation in [`labs/geoip-enrichment.md`](labs/geoip-enrichment.md).

Geolocation should be treated as contextual enrichment, not proof of a person's physical location or identity.

## Monitoring Results Used in the Case Study

One documented monitoring window contained:

- **663,762 total security alerts**,
- **37,433 authentication successes**,
- **2,852 authentication failures**,
- **6 alerts at level 12 or above**.

The material also documented rule-triggered activity involving authentication failures, web-security alerts, file-integrity changes, SQL-injection attempt alerts, Shellshock-related activity, rootcheck findings, and other endpoint/security telemetry.

These are monitoring observations and rule matches, not automatically confirmed incidents.

## Mandatory Redaction Checklist

Before publishing any additional screenshot or configuration, check for:

- internal IPv4/IPv6 addresses,
- public server addresses that identify organizational infrastructure,
- internal hostnames and DNS names,
- endpoint or agent names tied to the organization,
- dashboard URLs exposing private addressing,
- email addresses,
- student or employee identifiers,
- usernames where they reveal real infrastructure context,
- API keys, passwords, tokens, cookies, or session values,
- SMTP, MaxMind, VirusTotal, Graylog, OpenSearch, or other secrets,
- organization-specific paths or URLs,
- raw logs containing user or system-identifying data,
- unrelated browser tabs exposing internal systems.

Use placeholders where needed:

```text
<INTERNAL_IP>
<PUBLIC_SERVER_IP>
<MANAGER_HOST>
<API_KEY>
<PASSWORD>
security@example.org
```

## Evidence Integrity

Sanitization may hide sensitive identifiers, but it must **not change the meaning of the evidence**. Do not alter alert counts, chart values, severity distributions, or other measurements merely to make the project appear stronger.

The repository preserves three evidence classes:

1. **Final implementation evidence** — supported by the internship report and final monitoring results.
2. **Lab / explored integrations** — supported by working notes and clearly labeled under `labs/`.
3. **Future improvements** — proposals that should not be described as completed work.

This distinction is intentional so the public portfolio remains technically credible and does not overstate production deployment.