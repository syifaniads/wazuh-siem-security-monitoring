# MISP Integration

## Purpose

MISP (Malware Information Sharing Platform) was used as a threat-intelligence component in the monitoring workflow.

The final report describes MISP as a platform for storing and managing indicators related to threats, such as suspicious IP addresses, domains, URLs, and file hashes.

## Role in the monitoring workflow

```mermaid
flowchart LR
    A[Security Events] --> B[Wazuh]
    B --> C[Investigation]
    C --> D[MISP]
    D --> E[Threat Indicator Context]
```

## Security value

MISP helps move investigation beyond a single alert by providing context around indicators of compromise. This can support:

- indicator enrichment
- threat correlation
- documenting suspicious indicators
- sharing threat intelligence in a structured format

## Portfolio scope

This public documentation does not expose private MISP events, organization-specific indicators, credentials, or internal integration endpoints.
