# File Integrity Monitoring

## Objective

Use Wazuh File Integrity Monitoring (FIM) to detect changes to monitored files, directories, and registry/configuration data.

## Why it matters

Unexpected changes to application files or system configuration can indicate:

- unauthorized administrative changes
- compromised application files
- persistence mechanisms
- configuration drift
- legitimate maintenance that still requires audit visibility

## Example configuration

```xml
<syscheck>
  <disabled>no</disabled>
  <scan_on_start>yes</scan_on_start>

  <directories>/etc,/usr/bin,/usr/sbin</directories>
  <directories>/bin,/sbin,/boot</directories>

  <directories check_all="yes"
               report_changes="yes"
               realtime="yes">
    /var/www/html
  </directories>
</syscheck>
```

A sanitized reusable version is available in [`../configs/wazuh/fim-example.xml`](../configs/wazuh/fim-example.xml).

## Validation approach

The implementation can be validated by modifying a monitored test file and confirming that a corresponding integrity event appears in Wazuh.

The documented monitoring results included rules such as:

| Rule | Description |
|---|---|
| 750 | Registry Value Integrity Checksum Changed |
| 550 | Integrity checksum changed |
| 554 | File added to the system |

The internship report also identified endpoints with comparatively high FIM activity and recommended further monitoring to determine whether changes represented normal operations or suspicious behavior.

## Engineering lesson

FIM alerts should not be treated as incidents by default. High change volume can be caused by updates, package changes, application deployments, or system processes. Useful FIM monitoring therefore depends on good path selection, baselining, and alert triage.
