# Sunset Header

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
