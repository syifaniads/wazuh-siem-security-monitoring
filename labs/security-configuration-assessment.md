# Security Configuration Assessment (SCA) Lab

> **Classification:** Internship lab / implementation notes.

## Objective

Use Wazuh Security Configuration Assessment (SCA) to evaluate endpoint configuration against security policy checks and identify settings that require remediation.

The internship notes reference the SCA ruleset stored on Linux endpoints under:

```text
/var/ossec/ruleset/sca/
```

An example policy file observed in the notes was a CIS-oriented Ubuntu policy.

## Wazuh Configuration Example

```xml
<sca>
  <enabled>yes</enabled>
  <scan_on_start>yes</scan_on_start>
  <interval>12h</interval>
  <skip_nfs>yes</skip_nfs>
</sca>
```

This enables SCA scanning at agent start and on a recurring interval.

## Example Remediation Workflow

The notes include an SSH hardening example involving authentication-related options such as `MaxAuthTries` and `MaxSessions`.

A safe portfolio representation is:

```text
1. Run/inspect the SCA assessment.
2. Identify a failed configuration check.
3. Review the relevant operating-system configuration.
4. Apply an approved remediation.
5. Restart/reload the affected service when required.
6. Re-run the assessment and verify the result.
```

Example SSH settings documented in the notes included:

```text
MaxAuthTries 4
MaxSessions 10
```

These values are shown as an internship example, not as universal hardening recommendations for every environment.

## Validation

Validation should compare SCA state before and after an approved configuration change. The expected evidence is a previously failing check becoming compliant after remediation and reassessment.

## Security Value

SCA supports:

- configuration-baseline visibility,
- identification of weak or non-compliant settings,
- repeatable configuration review,
- evidence for hardening and audit activities.

## Limitations

- A passing benchmark check does not prove a system is secure.
- Some benchmark recommendations may conflict with application or operational requirements.
- Remediation should be reviewed before being applied to production systems.
- The final internship report does not establish this lab as part of the final production deployment, so it is documented separately from the core implementation.
