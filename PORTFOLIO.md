# Portfolio Copy

This file contains concise, reusable descriptions of the project for a personal website, CV, LinkedIn, or application form.

## Project Title

**Wazuh SIEM Security Monitoring**

## One-Line Description

Implemented a centralized security monitoring environment using Wazuh with Graylog and MISP integrations, covering file-integrity monitoring, vulnerability detection, alert analysis, and security reporting.

## Short Portfolio Description

Built and evaluated a Wazuh-based SIEM environment for centralized endpoint monitoring during an internship. Configured File Integrity Monitoring, vulnerability detection, endpoint enrollment, Graylog integration, MISP-based threat-intelligence workflows, and email alerting. Analyzed a documented monitoring window containing more than **663K security alerts**, including authentication, file-integrity, web-security, and malware/rootcheck-related events.

## CV Version

**Wazuh SIEM Security Monitoring — Cybersecurity / Infrastructure Project**

- Implemented and configured centralized endpoint security monitoring using Wazuh, with Graylog and MISP integrations.
- Configured File Integrity Monitoring, vulnerability detection, event collection, and email-based security alerting.
- Analyzed 663K+ rule-triggered security events, including 37K+ successful authentication events and 2.8K+ authentication failures during a documented monitoring period.
- Reviewed web-security, file-integrity, authentication, malware/rootcheck, and endpoint events and mapped selected activity categories to MITRE ATT&CK.
- Documented security monitoring observations and reviewed Wazuh-generated compliance mappings for PCI DSS, GDPR, HIPAA, TSC, and NIST 800-53.

## Website Case Study Version

### Problem

Security events from multiple endpoints are difficult to investigate when logs and alerts are spread across individual systems. The project explored centralized monitoring to improve visibility into endpoint activity, file changes, vulnerabilities, authentication behavior, and security-related application events.

### Approach

I implemented a monitoring environment centered on Wazuh agents and a Wazuh Manager/Indexer/Dashboard stack. Security data was reviewed centrally, with Graylog used for additional log visualization and MISP incorporated into the threat-intelligence workflow. Email notification was also configured to support operational alerting.

### Analysis

During one documented monitoring window, the system recorded **663,762 security alerts**, including **37,433 authentication successes** and **2,852 authentication failures**. I reviewed alert categories covering authentication behavior, web-server activity, file-integrity changes, rootcheck/malware indicators, and other endpoint events.

Rule-triggered alerts such as SQL-injection attempts, Shellshock-related activity, CMS login/brute-force indicators, and possible rootkit detections were treated as signals requiring investigation rather than automatically classified as confirmed compromises.

### Outcome

The project produced a centralized security-monitoring workflow and practical experience with SIEM configuration, endpoint visibility, log analysis, threat-intelligence integration, MITRE ATT&CK mapping, and security-report interpretation.

## Technology Tags

`Wazuh` · `SIEM` · `Linux` · `Cybersecurity` · `Graylog` · `MISP` · `MITRE ATT&CK` · `File Integrity Monitoring` · `Vulnerability Detection` · `Log Analysis` · `Security Monitoring`

## Recommended Portfolio Link Label

**View Technical Case Study on GitHub**

## Interview Talking Points

A concise interview explanation can follow this order:

1. **Problem:** security telemetry was distributed across endpoints and required centralized visibility.
2. **Architecture:** endpoints send telemetry through Wazuh agents to the Wazuh monitoring stack; Graylog, MISP, and email alerting support analysis and operations.
3. **Your contribution:** configuration, agent enrollment, FIM, vulnerability monitoring, log analysis, integration work, and documentation.
4. **Evidence:** 663K+ alerts in the documented monitoring period and analysis across multiple event categories.
5. **Engineering lesson:** an alert is not the same as a confirmed incident; context, baselining, false-positive review, and prioritization are necessary.

## Accuracy Note

The public repository separates the final implementation from additional internship labs. Do not describe every item under `labs/` as production deployed unless additional evidence supports that claim.
