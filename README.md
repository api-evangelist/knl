# KNL

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
