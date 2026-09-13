# Wazuh Agent Enrollment

## Objective

Register monitored endpoints with the Wazuh Manager so agents can authenticate, receive configuration, and send security telemetry to the centralized monitoring environment.

The internship working notes covered enrollment through agent configuration and also referenced enrollment through the Wazuh server API.

## Password-Authenticated Enrollment

The notes used password authentication as an additional enrollment control.

### Manager-side example

```xml
<auth>
  <use_password>yes</use_password>
</auth>
```

The enrollment password is stored in a protected file rather than committed into configuration or source control.

```bash
sudo sh -c 'printf "%s\n" "<ENROLLMENT_PASSWORD>" > /var/ossec/etc/authd.pass'
sudo chmod 640 /var/ossec/etc/authd.pass
sudo chown root:wazuh /var/ossec/etc/authd.pass
sudo systemctl restart wazuh-manager
```

### Agent-side example

```xml
<client>
  <enrollment>
    <authorization_pass_path>/var/ossec/etc/authd.pass</authorization_pass_path>
  </enrollment>
</client>
```

The agent uses its own protected `authd.pass` file containing the same enrollment secret.

```bash
sudo chmod 640 /var/ossec/etc/authd.pass
sudo chown root:wazuh /var/ossec/etc/authd.pass
sudo systemctl restart wazuh-agent
```

A sanitized XML example is available in [`../configs/wazuh/agent-enrollment-example.xml`](../configs/wazuh/agent-enrollment-example.xml).

## Validation Approach

After enrollment:

1. confirm the agent service is running,
2. confirm the endpoint appears in the Wazuh agent inventory,
3. confirm its state becomes active/connected,
4. verify events from the endpoint appear in the central monitoring interface,
5. review manager/agent logs if enrollment fails.

## Security Considerations

Enrollment credentials should be handled like secrets:

- never commit `authd.pass`,
- restrict file permissions,
- rotate the enrollment password if it is exposed,
- verify manager identity when supported by the deployment design,
- avoid using a shared enrollment secret longer than operationally necessary.

## Portfolio Scope

This page documents the enrollment workflow reflected in the internship working notes. Real manager addresses, endpoint names, and enrollment secrets are intentionally omitted.