# Security and Responsible Publishing

This repository contains sanitized security engineering documentation.

## What must never be committed

Do not commit:

- passwords, access tokens, API keys, SMTP credentials, or private keys
- real internal IP addresses or VPN-accessible infrastructure details
- organization-specific hostnames when they reveal internal topology
- raw logs containing usernames, endpoint names, source IPs, or sensitive paths
- screenshots that expose credentials, private infrastructure, or confidential dashboards

## Placeholder convention

Use placeholders such as:

```text
<MANAGER_IP>
<AGENT_IP>
<SMTP_USER>
<SMTP_PASSWORD>
<API_KEY>
<INTERNAL_HOST>
```

For topology examples, prefer documentation-only RFC/private examples or generic labels rather than real production values.

## Alert interpretation

A Wazuh alert represents a rule match or monitoring observation. It should not automatically be described as a confirmed attack or incident without investigation and contextual validation.

## Reporting a problem

If sensitive information is accidentally committed, remove it from the repository history and rotate affected credentials immediately.
