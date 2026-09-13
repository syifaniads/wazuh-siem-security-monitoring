# Additional Security Labs

The internship working notes include a broader set of security configurations and integration experiments than the final implementation report.

They are listed separately here to avoid overstating what was part of the final deployed monitoring stack.

## Available Lab Notes

| Lab | Focus |
|---|---|
| [Suricata IDS/IPS Integration](suricata-integration.md) | Network-level detection forwarded into Wazuh |
| [Security Configuration Assessment](security-configuration-assessment.md) | SCA/CIS-style configuration assessment and remediation workflow |
| [ClamAV Integration](clamav-integration.md) | Malware scanning and file-event monitoring concept |
| [Docker Monitoring](docker-monitoring.md) | Wazuh Docker listener and container activity visibility |
| [GeoIP Enrichment](geoip-enrichment.md) | GeoLite2-based country/city/ASN enrichment |
| [Active Response](active-response.md) | Rule-triggered automated response concept |
| [VirusTotal Integration](virustotal-integration.md) | File reputation enrichment from FIM events |
| [Index Lifecycle Management](index-lifecycle-management.md) | Hot/warm/delete lifecycle for Wazuh alert indices |

The original working notes also covered endpoint enrollment with password authentication, Wazuh archives, SMTP-based alerting, and additional Graylog/MISP setup notes. Some of those topics are already represented in the core documentation or may be added as separate labs later.

## Evidence Classification

These topics are best described as **labs, implementation notes, or explored integrations** unless separately validated by final deployment evidence.

Each lab is written using a consistent engineering format:

1. Objective
2. Architecture / data flow
3. Sanitized configuration
4. Validation method
5. Expected result
6. Security value
7. Limitations / operational considerations

This keeps the repository useful while preserving a clear boundary between final implementation evidence and experimental work.

## Safe Reuse

All values that could identify the original environment should be replaced with placeholders. Do not commit credentials, API keys, internal hostnames, internal IP addresses, or raw production logs.
