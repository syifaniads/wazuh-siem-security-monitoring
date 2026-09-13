# GeoIP Enrichment Lab

> **Classification:** Internship lab / implementation notes.

## Objective

Enrich security events with geographic context using MaxMind GeoLite2 data so source IP addresses can be associated with country/city/ASN information during investigation.

## Concept

```mermaid
flowchart LR
    A[Security Event with Source IP] --> B[Wazuh / Indexer]
    C[GeoLite2 Databases] --> B
    B --> D[Enriched Event]
    D --> E[Country / City / ASN Context]
    D --> F[Wazuh Maps]
```

The internship notes used MaxMind GeoLite2 databases and the Wazuh Indexer GeoIP ingest module.

## GeoLite2 Update Setup

Example installation flow:

```bash
sudo apt update
sudo apt install geoipupdate -y
```

A sanitized `/etc/GeoIP.conf` example:

```text
AccountID <MAXMIND_ACCOUNT_ID>
LicenseKey <MAXMIND_LICENSE_KEY>
EditionIDs GeoLite2-City GeoLite2-Country GeoLite2-ASN
```

Update and verify the local databases:

```bash
sudo geoipupdate -v
ls -l /usr/share/GeoIP/
```

Expected database families include City, Country, and ASN data.

## Indexer Integration Notes

The working notes copied GeoLite2 databases to the Wazuh Indexer ingest-geoip module directory and adjusted ownership before restarting the indexer.

Sanitized example:

```bash
sudo mkdir -p /usr/share/wazuh-indexer/modules/ingest-geoip/
sudo cp -r /usr/share/GeoIP/* /usr/share/wazuh-indexer/modules/ingest-geoip/
sudo chown -R wazuh-indexer:wazuh-indexer /usr/share/wazuh-indexer/modules/ingest-geoip/Geo*
sudo systemctl restart wazuh-indexer
```

## Wazuh Maps Validation

The reviewed visual evidence shows a Documents layer configured with:

```text
Index pattern: wazuh-alerts-*
Geospatial field: GeoLocation.location
```

A separate working screenshot shows an enriched event plotted in the East Java area. This demonstrates that geographic fields were available to Wazuh Maps and could be used for visualization.

```mermaid
flowchart LR
    A[wazuh-alerts-*] --> B[GeoLocation.location]
    B --> C[Documents Layer]
    C --> D[Wazuh Map]
```

## Validation Approach

1. Confirm GeoLite2 databases are present.
2. Confirm the indexer starts successfully after the database update.
3. Verify the GeoIP ingest module is available.
4. Inspect events containing public source IP addresses.
5. Confirm geographic fields are populated where data is available.
6. Create a Wazuh Maps layer from `wazuh-alerts-*` using `GeoLocation.location`.
7. Confirm enriched documents can be rendered as map points.

## Public Portfolio Evidence

The original working material includes both map and layer-configuration screenshots. They are **not included in the current public screenshot set** because the portfolio already has stronger high-level evidence and because additional captures increase the chance of exposing environment-specific data.

The configuration details supported by those screenshots are preserved above in text form. The public visual set is documented in [`../screenshots/README.md`](../screenshots/README.md).

## Security Value

GeoIP context can help analysts:

- quickly understand the geographic origin associated with public IP telemetry,
- group or filter alerts by region,
- add context to authentication or web-security investigations,
- identify unusual geographic patterns for further review.

## Interpretation Warning

Geolocation is **context, not proof of attacker identity or physical location**. VPNs, proxies, cloud providers, carrier networks, NAT, and database accuracy can all affect results.

## Privacy & Repository Safety

Do not publish real MaxMind credentials or raw internal event data. Portfolio examples should use placeholders and, where screenshots are added in the future, redact internal addresses and organizational identifiers.

See [`../EVIDENCE.md`](../EVIDENCE.md) for the repository-wide evidence policy.