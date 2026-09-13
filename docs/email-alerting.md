# Email Alerting

## Objective

Provide an operational notification path so selected Wazuh alerts can be delivered by email instead of requiring an administrator to watch the dashboard continuously.

The internship notes configured Wazuh email notification together with an SMTP relay and severity thresholds.

## Sanitized Wazuh Example

```xml
<ossec_config>
  <global>
    <email_notification>yes</email_notification>
    <smtp_server><SMTP_RELAY></smtp_server>
    <email_from><ALERT_SENDER></email_from>
    <email_to><ALERT_RECIPIENT></email_to>
    <email_maxperhour>12</email_maxperhour>
  </global>

  <alerts>
    <log_alert_level>3</log_alert_level>
    <email_alert_level>8</email_alert_level>
  </alerts>
</ossec_config>
```

A reusable sanitized example is available in [`../configs/wazuh/alerting-example.xml`](../configs/wazuh/alerting-example.xml).

## SMTP Relay Notes

The working notes used a local mail-transfer agent as the relay path to an external SMTP provider. Public portfolio documentation intentionally omits:

- real sender/recipient addresses,
- SMTP usernames and passwords,
- internal hostnames,
- environment-specific mail-server configuration.

Credentials should be stored outside version control and protected with restrictive file permissions.

## Validation Approach

1. Enable Wazuh email notification.
2. Configure the relay and sender/recipient placeholders with valid environment values.
3. Trigger or identify an alert above the configured email threshold.
4. Confirm the notification is delivered.
5. Review Wazuh and mail-relay logs if delivery fails.
6. Confirm rate limits are appropriate so alert storms do not flood the recipient.

## Operational Considerations

Email is useful as a notification channel, but it should not become the only incident-response mechanism. Useful controls include:

- severity thresholds,
- rate limiting,
- distribution lists rather than personal inboxes where appropriate,
- documented escalation paths,
- monitoring for mail delivery failures.

## Portfolio Scope

The final implementation material includes email alerting as part of the monitoring workflow. All real addresses and SMTP credentials have been removed from this public repository.