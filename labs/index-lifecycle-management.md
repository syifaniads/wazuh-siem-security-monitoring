# Wazuh Index Lifecycle Management Lab

> **Classification:** Internship lab / implementation notes.

## Objective

Explore index lifecycle management for Wazuh alert data so storage can be managed through rollover, optimization, and deletion policies.

The internship notes describe a policy for `wazuh-alerts-*` indices with three conceptual phases:

1. **Hot** — new alert data is actively written.
2. **Warm** — older data is accessed less frequently and can be optimized.
3. **Delete** — old indices are removed after the configured retention period.

```mermaid
flowchart LR
    A[Hot Phase] --> B[Warm Phase]
    B --> C[Delete Phase]
```

## Policy Example

A simplified, sanitized version based on the working notes:

```json
{
  "policy": {
    "policy_id": "wazuh-alerts-ilm",
    "description": "Rollover and retention policy for Wazuh alert indices",
    "default_state": "Hot Phase",
    "states": [
      {
        "name": "Hot Phase",
        "actions": [
          {
            "rollover": {
              "min_size": "500mb",
              "min_doc_count": 5,
              "min_index_age": "1d"
            }
          }
        ],
        "transitions": [
          { "state_name": "Warm Phase" }
        ]
      },
      {
        "name": "Warm Phase",
        "actions": [
          {
            "force_merge": {
              "max_num_segments": 1
            }
          }
        ],
        "transitions": [
          {
            "state_name": "Delete Phase",
            "conditions": {
              "min_index_age": "30d"
            }
          }
        ]
      },
      {
        "name": "Delete Phase",
        "actions": [
          { "delete": {} }
        ],
        "transitions": []
      }
    ],
    "ism_template": [
      {
        "index_patterns": ["wazuh-alerts-*"],
        "priority": 1
      }
    ]
  }
}
```

The values above reproduce the policy concept documented in the internship notes. They should not be treated as universal production retention recommendations.

## Why Lifecycle Management Matters

Security monitoring can generate large amounts of event data. Without retention planning, an indexer may eventually consume excessive disk space, which can affect availability and query performance.

Lifecycle management helps define:

- when an index rolls over,
- how older indices are optimized,
- how long alert data is retained,
- when old data is deleted.

## Validation Approach

1. Create/apply the policy in a test environment.
2. Confirm the policy matches the intended `wazuh-alerts-*` indices.
3. Verify index state transitions.
4. Monitor disk usage and index health.
5. Confirm deletion occurs only after the intended retention period.

## Operational Considerations

Retention should be selected according to organizational requirements, storage capacity, forensic needs, backup strategy, and applicable policy/compliance requirements.

Deleting security telemetry too early can reduce investigation capability, while retaining everything indefinitely can create unnecessary storage and performance costs.
