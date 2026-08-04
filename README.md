# KNL

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

KNL (KNL Networks Oy) is a Finnish defence-technology company founded in 2011 and headquartered in Oulu,
Finland. It builds long-range, GNSS-independent HF radio communication systems for military, naval, and
critical-communications operators. Its Cognitive Networked HF (CNHF) platform is a family of software-defined
radios — CNHF Manpack, CNHF1 Radio, CNHF Vehicular, and CNHF Evolve — that perform continuous spectrum
estimation and automatically switch to the next best channel to sustain IP data links over thousands of
kilometres in jammed, contested, or infrastructure-denied environments.

Radios are operated through a web-based CNHF User Interface offering role-based access (Admin/User/Monitor),
webmail, XMPP-interoperable instant messaging, real-time mapping, spectrum analysis, and EMCON mode
selection.

KNL was acquired by Telenor Maritime at the end of 2020 and now operates as Telenor's dedicated defence and
security connectivity business.

- Website: https://knl.fi/ (knlnetworks.com 301-redirects here)
- Products: https://knl.fi/products/
- Newsroom: https://knl.fi/newsroom/
- Careers: https://careers.knl.fi/

Backed by: creandum (Series A, 2016, $10M — led by Creandum with Inventure and Butterfly Ventures)

## No public API surface

KNL publishes **no public developer API, OpenAPI specification, developer portal, documentation site, SDK, or
CLI**. This is expected for a defence hardware vendor selling to sovereign customers under export control.
Verified absent as of 2026-07-19:

- `api.knl.fi`, `developer.knl.fi`, `docs.knl.fi`, `status.knl.fi`, `trust.knl.fi` — do not resolve
- All `/.well-known/` discovery documents — 404
- `github.com/KNLNetworks` — org exists and is first-party, but has zero public repositories
- npm, PyPI, Maven Central, NuGet, crates.io, RubyGems, Packagist — no first-party packages

Consequently the spec-dependent artifacts in the enrichment pipeline (`openapi/`, `overlays/`, `errors/`,
`scopes/`, `authentication/`, `mcp/`, `skills/`, `data-model/`, `conventions/`, `sandbox/`, `cli/`,
`components/`, `asyncapi/`, `grpc/`) are **intentionally absent rather than fabricated**.

## Artifacts present

| Path | Type | Method |
|---|---|---|
| `llms/knl-llms.txt` | LLMsTxt | searched — verbatim from https://knl.fi/llms.txt |
| `conformance/knl-conformance.yml` | Conformance + Compliance | searched — ISO 9001, AQAP 2110, ISO/IEC 27001, MIL-STD-810H, AES-256, XMPP |
| `security/knl-domain-security.yml` | DomainSecurity | probed — TLS 1.3, SPF, DMARC (p=none); no HSTS, no DNSSEC, no CAA |
| `well-known/knl-well-known.yml` | — (negative record) | probed |
| `packages/knl-packages.yml` | — (negative record) | searched |

The two negative records carry no `apis.yml` pointer; they exist so re-runs of the pipeline do not re-probe
a surface already confirmed empty.
