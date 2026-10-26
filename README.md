# We > Ultrarich (wegtultrarich)

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

A free, non-commercial tool and public API that visualize extreme wealth inequality by comparing any wealth to ultrarich/billionaire/trillionaire wealth through four lenses: Duration Of Daily Spend, Height Of Stacked Money, Number Of Items Paid For, and Growth Of Compound Interest. All comparisons are deterministic arithmetic returning ready-to-quote figures, sentences, and them-vs-you ratios; no user data is collected. The surface is agent-native: a no-auth OpenAPI 3.0.4 REST API, a hosted Streamable-HTTP MCP server exposing the same five computations as tools, llms.txt and llms-full.txt, a published agent prompt, an APIs.json 0.21 index, and the Spectral ruleset the spec is linted against. Published by Blonde Rocket Scientist LLC; results are licensed CC BY 4.0 with a required attribution string.

**APIs.json:** [https://api.wegtultrarich.org/apis.json](https://api.wegtultrarich.org/apis.json)

## Tags

- wealth inequality
- economic inequality
- finance
- economics
- education
- journalism
- open data
- comparison
- mcp
- model context protocol
- agents

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-08-09

## APIs

### We > Ultrarich MCP Server

Hosted, no-auth Model Context Protocol server (Streamable HTTP) exposing the same five wealth computations as agent tools with published JSON Schema inputs. Answers protocol revisions 2025-03-26 through 2026-07-28 from one endpoint, holds no session state, and returns the bare data object plus an attribution string. Rate limited to 300 requests per minute per IP.

- **Human URL:** [https://api.wegtultrarich.org/README.md#mcp-server](https://api.wegtultrarich.org/README.md#mcp-server)
- **Base URL:** `https://api.wegtultrarich.org/mcp`

#### Tags

- mcp
- model context protocol
- agents
- wealth inequality
- comparison

#### Properties

- [M C P Server](mcp/wegtultrarich-mcp.yml)
- [M C P](https://api.wegtultrarich.org/mcp)
- [Tool Crosswalk](mcp/wegtultrarich-tool-crosswalk.yml)
- [Model Context Protocol](https://api.wegtultrarich.org/.well-known/mcp.json)
- [Postman Collection](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp-server/collection/6a68bfdcf1d9df57e26c3545) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Documentation](https://api.wegtultrarich.org/README.md#mcp-server)
- [Postman Collection](collections/wegtultrarich-comparison-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-comparison-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/wegtultrarich-discovery-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-discovery-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/wegtultrarich-wealth-expression-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-wealth-expression-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### We > Ultrarich Comparison API

Compare any wealth expression for two wealths ('yours' and 'theirs') in a single call — get both results as well as the ratio between them.

- **Human URL:** [https://api.wegtultrarich.org/](https://api.wegtultrarich.org/)
- **Base URL:** `https://api.wegtultrarich.org/v1`

#### Tags

- Comparison

#### Properties

- [OpenAPI](openapi/wegtultrarich-comparison-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/wegtultrarich-comparison-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-comparison-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [OpenAPI](https://api.wegtultrarich.org/openapi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.wegtultrarich.org/README.md)
- [API Reference](https://api.wegtultrarich.org/)
- [Getting Started](https://api.wegtultrarich.org/README.md#quick-start)
- [Postman Collection](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp-server/collection/kcacxo9/start-here-four-ways-to-understand-extreme-wealth) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Examples](examples/_index.yml)
- [Arazzo](arazzo/wegtultrarich-wealth-inequality-briefing.yml) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)

### We > Ultrarich Discovery API

Discover (list) the available endpoints.

- **Human URL:** [https://api.wegtultrarich.org/](https://api.wegtultrarich.org/)
- **Base URL:** `https://api.wegtultrarich.org/v1`

#### Tags

- Discovery

#### Properties

- [OpenAPI](openapi/wegtultrarich-discovery-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/wegtultrarich-discovery-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-discovery-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://api.wegtultrarich.org/README.md)
- [API Reference](https://api.wegtultrarich.org/)
- [Getting Started](https://api.wegtultrarich.org/README.md#quick-start)
- [Postman Collection](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp-server/collection/kcacxo9/start-here-four-ways-to-understand-extreme-wealth) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Examples](examples/_index.yml)
- [Arazzo](arazzo/wegtultrarich-wealth-inequality-briefing.yml) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)

### We > Ultrarich Wealth Expression API

Express a single wealth through one of four lenses (daily spending, physical size, purchasing power, or compound interest).

- **Human URL:** [https://api.wegtultrarich.org/](https://api.wegtultrarich.org/)
- **Base URL:** `https://api.wegtultrarich.org/v1`

#### Tags

- Wealth Expression

#### Properties

- [OpenAPI](openapi/wegtultrarich-wealth-expression-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/wegtultrarich-wealth-expression-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/wegtultrarich-wealth-expression-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://api.wegtultrarich.org/README.md)
- [API Reference](https://api.wegtultrarich.org/)
- [Getting Started](https://api.wegtultrarich.org/README.md#quick-start)
- [Postman Collection](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp-server/collection/kcacxo9/start-here-four-ways-to-understand-extreme-wealth) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Examples](examples/_index.yml)
- [Arazzo](arazzo/wegtultrarich-wealth-inequality-briefing.yml) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)

## Common Properties

- [M C P Server](mcp/wegtultrarich-mcp.yml)
- [Status Page](https://wegtultrarich.instatus.com/)
- [Pricing](https://wegtultrarich.org/pricing.html)
- [Overlay](overlays/wegtultrarich-openapi-overlay.yaml)
- [Website](https://wegtultrarich.org/)
- [Developer Portal](https://api.wegtultrarich.org/)
- [Documentation](https://api.wegtultrarich.org/README.md)
- [API Reference](https://api.wegtultrarich.org/openapi.yaml)
- [Getting Started](https://api.wegtultrarich.org/README.md#quick-start)
- [Support](https://wegtultrarich.org/faq.html)
- [F A Q](https://wegtultrarich.org/faq.html)
- [About](https://wegtultrarich.org/about.html)
- [Contact](https://wegtultrarich.org/partners.html)
- [Postman](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp-server/collection/kcacxo9/start-here-four-ways-to-understand-extreme-wealth) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Terms of Service](https://wegtultrarich.org/terms-of-use.html)
- [Privacy Policy](https://wegtultrarich.org/privacy-policy.html)
- [License](https://wegtultrarich.org/LICENSE.md)
- [Changelog](https://wegtultrarich.org/CHANGELOG.md)
- [Changelog](changelog/wegtultrarich-changelog.yml)
- [Lifecycle](lifecycle/wegtultrarich-lifecycle.yml)
- [Security](https://wegtultrarich.org/SECURITY.md)
- [Vulnerability Disclosure](security/wegtultrarich-vulnerability-disclosure.yml)
- [Security Txt](https://api.wegtultrarich.org/.well-known/security.txt)
- [Domain Security](security/wegtultrarich-domain-security.yml)
- [Well Known](well-known/wegtultrarich-well-known.yml)
- [Authentication](authentication/wegtultrarich-authentication.yml)
- [Conventions](conventions/wegtultrarich-conventions.yml)
- [Idempotency](conventions/wegtultrarich-conventions.yml)
- [Error Catalog](errors/wegtultrarich-problem-types.yml)
- [Rate Limits](rate-limits/wegtultrarich-rate-limits.yml)
- [Conformance](conformance/wegtultrarich-conformance.yml)
- [Vocabulary](vocabulary/wegtultrarich-vocabulary.yml)
- [Data Model](data-model/wegtultrarich-data-model.yml)
- [Packages](packages/wegtultrarich-packages.yml)
- [Rules](rules/wegtultrarich-spectral.yaml)
- [Agent Skill](skills/_index.yml)
- [Agent Prompt](skills/wegtultrarich-agent-prompt.md)
- [Agentic Access](agentic-access/wegtultrarich-agentic-access.yml)
- [L L Ms Txt](llms/wegtultrarich-llms.txt)
- [L L Ms Txt](https://wegtultrarich.org/llms.txt)
- [L L Ms Txt](https://wegtultrarich.org/llms-full.txt)
- [A P Is J S O N](https://api.wegtultrarich.org/apis.json)

## Maintainers

**FN:** Blonde Rocket Scientist LLC
**Email:** info@wegtultrarich.org
**URL:** https://wegtultrarich.org/
