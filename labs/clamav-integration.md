# ClamAV Integration Lab

> **Classification:** Internship lab / implementation notes.

## Objective

Combine Wazuh endpoint monitoring with ClamAV malware scanning so malware-related scan results can be observed alongside other endpoint security telemetry.

The working notes describe ClamAV as an open-source antivirus engine used to detect viruses, trojans, malware, and other malicious files.

## Installation & Update Flow

Example commands documented during the internship:

```bash
sudo apt update
sudo apt install clamav-daemon

sudo systemctl stop clamav-freshclam.service
sudo freshclam
sudo systemctl start clamav-freshclam.service
```

Manual scanning examples:

```bash
sudo clamscan <PATH>
sudo clamdscan --fdpass <PATH>
```

## Wazuh Log Collection

The notes include collecting system logs through Wazuh using sources such as syslog or journald.

Example:

```xml
<localfile>
  <log_format>syslog</log_format>
  <location>/var/log/syslog</location>
</localfile>

<localfile>
  <log_format>journald</log_format>
  <location>journald</location>
</localfile>
```

## Real-Time File Event Concept

The internship notes also explored `inotify-tools` to react when new files are created in a monitored directory and then submit them to ClamAV for scanning.

Example sanitized workflow:

```bash
sudo apt install inotify-tools -y
```

```bash
#!/bin/bash
MONITORED_DIR="<MONITORED_DIRECTORY>"

inotifywait -m -r -e create --format '%w%f' "$MONITORED_DIR" | while read NEWFILE
do
  echo "New file detected: $NEWFILE"
  clamdscan --fdpass "$NEWFILE"
done
```

The script path and monitored directory should be chosen for an authorized lab environment.

## Validation Approach

A safe lab validation flow is:

1. Confirm the ClamAV daemon and signature updater are healthy.
2. Scan a benign test file or approved anti-malware test artifact.
3. Confirm ClamAV produces a detection/log event as expected.
4. Confirm the relevant event source is visible to Wazuh.
5. Review the event in the centralized monitoring interface.

## Security Value

This lab demonstrates how file-based malware scanning can complement Wazuh's host monitoring, FIM, and other endpoint detections.

## Limitations

- Signature-based detection cannot identify every malicious file.
- File-system monitoring and continuous scanning can increase resource usage.
- Alerting should distinguish scan results, operational errors, and confirmed malicious findings.
- The available final report does not establish this integration as part of the final production stack, so it remains classified as a lab.
