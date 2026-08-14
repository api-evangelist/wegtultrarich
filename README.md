# We > Ultrarich (wegtultrarich)

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
- [Postman Collection](https://www.postman.com/wegtultrarich/we-ultrarich-extreme-wealth-api-mcp/collection/6a68bfdcf1d9df57e26c3545) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
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
