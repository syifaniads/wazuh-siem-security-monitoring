# Docker Container Monitoring Lab

> **Classification:** Internship lab / implementation notes.

## Objective

Explore Wazuh monitoring for Docker activity so container-related events can be included in centralized security monitoring.

## Environment Setup

The internship notes document installing Docker and Python dependencies required by the Wazuh Docker listener integration.

Example installation flow:

```bash
curl -sSL https://get.docker.com/ | sh
sudo systemctl status docker.service
```

The original notes also pinned Python packages for compatibility with the environment used during testing. Those exact versions are intentionally not treated as universal requirements here because package compatibility can change over time.

## Wazuh Docker Listener

Example configuration from the working notes:

```xml
<ossec_config>
  <wodle name="docker-listener">
    <interval>10m</interval>
    <attempts>5</attempts>
    <run_on_start>yes</run_on_start>
    <disabled>no</disabled>
  </wodle>
</ossec_config>
```

After updating the agent configuration:

```bash
sudo systemctl restart wazuh-agent
```

## Validation Example

The notes validated Docker activity using a disposable Nginx container:

```bash
sudo docker pull nginx
sudo docker run -d -P --name nginx_container nginx
sudo docker exec -it nginx_container cat /etc/passwd
```

Cleanup:

```bash
sudo docker stop nginx_container
sudo docker rm nginx_container
```

The purpose of this test is not to attack the container, but to generate legitimate container lifecycle/activity events that can be observed by the monitoring pipeline.

## Expected Result

A successful lab should demonstrate that Docker-related activity becomes visible to Wazuh and can be correlated with endpoint events from the same host.

## Security Value

Container monitoring can improve visibility into:

- container start/stop activity,
- administrative actions,
- workload changes,
- events that may otherwise be hidden when focusing only on the host operating system.

## Limitations

- The final internship report does not establish Docker monitoring as part of the final production deployment.
- Container telemetry alone is not a complete container-security strategy.
- Production environments should also consider image provenance, runtime controls, secrets handling, network policy, and orchestrator-level visibility where applicable.
