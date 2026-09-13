# Reports and Evidence

The original internship material contains Wazuh-generated monitoring reports and organizational infrastructure details.

Raw exports are **not published directly** in this public repository because they contain endpoint names, addresses, internal topology information, user/context data, and other operational details.

Instead, this repository publishes sanitized summaries of the findings in [`../docs/monitoring-analysis.md`](../docs/monitoring-analysis.md).

## Documented summary values

One monitoring window reported:

- 663,762 total security alerts
- 37,433 successful authentication events
- 2,852 failed authentication events
- 6 alerts at level 12 or above

The underlying reports also contained security-rule matches for authentication failures, web activity, file integrity changes, SQL injection attempts, Shellshock-related activity, rootcheck findings, and other system/security telemetry.

## Future evidence additions

Screenshots may be added later only after sanitization. Before committing any screenshot:

1. hide real IP addresses
2. hide hostnames that reveal internal infrastructure
3. remove usernames and email addresses where appropriate
4. remove credentials, tokens, keys, and session information
5. verify browser tabs, URLs, and side panels do not expose confidential data
6. add a caption explaining what the screenshot demonstrates

The goal is to provide enough evidence for a technical portfolio without disclosing the original organization's sensitive environment.
