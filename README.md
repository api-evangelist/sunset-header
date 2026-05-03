# Sunset Header

The Sunset HTTP header field (RFC 8594) is an IETF standard that allows servers to communicate to clients that a URI is likely to become unresponsive at a specified future point in time.

Published in May 2019, it provides a standardized mechanism for API deprecation signaling, enabling clients to plan migrations before service retirement.

## Specifications

| RFC | Title | Status |
|-----|-------|--------|
| [RFC 8594](https://www.rfc-editor.org/rfc/rfc8594) | The Sunset HTTP Header Field | Informational (2019) |
| [RFC 9745](https://www.rfc-editor.org/rfc/rfc9745) | The Deprecation HTTP Response Header Field | Proposed Standard (2025) |

## Header Syntax

```
# Sunset header (RFC 8594) — HTTP-date format
Sunset: Sat, 31 Dec 2026 23:59:59 GMT

# Deprecation header (RFC 9745) — Unix timestamp
Deprecation: @1688169599

# Link headers for documentation references
Link: <https://developer.example.com/migration>; rel="deprecation"
Link: <https://developer.example.com/sunset-policy>; rel="sunset"
```

## API Lifecycle

The two headers enable a two-phase deprecation lifecycle:

1. **Deprecation** — The `Deprecation` header marks when an endpoint enters the deprecated state. It is still operational but scheduled for removal.
2. **Sunset** — The `Sunset` header marks the end-of-life date. After this date, the server may return `410 Gone` or become unresponsive.

The `Sunset` timestamp must not be earlier than the `Deprecation` timestamp.

## Artifacts

| Type | File |
|------|------|
| JSON Schema | [sunset-header-schema.json](json-schema/sunset-header-schema.json) |
| JSON-LD Context | [sunset-header-context.jsonld](json-ld/sunset-header-context.jsonld) |
| Example Response | [sunset-header-response-example.json](examples/sunset-header-response-example.json) |
| Vocabulary | [sunset-header-vocabulary.yml](vocabulary/sunset-header-vocabulary.yml) |

## Tags

API Deprecation, HTTP Headers, RFC 8594, RFC 9745, API Lifecycle, REST APIs, Standards
