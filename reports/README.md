# Reports and Evidence

The original internship material contains Wazuh-generated monitoring reports and organization-specific infrastructure details.

Raw exports are **not published directly** in this public repository because they contain endpoint names, addresses, internal topology information, user/context data, and other operational details.

Instead, this repository publishes:

- sanitized summaries in [`../docs/monitoring-analysis.md`](../docs/monitoring-analysis.md),
- a repository-wide evidence guide in [`../EVIDENCE.md`](../EVIDENCE.md),
- two sanitized dashboard screenshots in [`../screenshots/`](../screenshots/README.md).

## Documented Summary Values

One monitoring window reported:

- **663,762 total security alerts**,
- **37,433 successful authentication events**,
- **2,852 failed authentication events**,
- **6 alerts at level 12 or above**.

The underlying reports also contained security-rule matches for authentication failures, web activity, file-integrity changes, SQL-injection attempts, Shellshock-related activity, rootcheck findings, and other system/security telemetry.

These values describe the documented monitoring period and should not be interpreted as permanent project-wide totals.

## Published Visual Evidence

The public repository currently includes only:

- `wazuh-overview-dashboard-sanitized.png`,
- `wazuh-mitre-attack-dashboard-sanitized.png`.

This limited set is intentional. It provides visible proof of the monitoring environment and ATT&CK-oriented analysis while minimizing the risk of disclosing internal infrastructure information.

## Sanitization Rules for Future Evidence

Before adding any additional screenshot or report extract:

1. hide real IP addresses,
2. hide hostnames that reveal internal infrastructure,
3. remove usernames and email addresses where appropriate,
4. remove credentials, tokens, keys, cookies, and session information,
5. verify browser tabs, URLs, and side panels do not expose confidential data,
6. preserve the original meaning, counts, and chart values,
7. add a caption explaining what the evidence demonstrates.

The goal is to provide enough evidence for a technical portfolio without publishing the original organization's sensitive environment.