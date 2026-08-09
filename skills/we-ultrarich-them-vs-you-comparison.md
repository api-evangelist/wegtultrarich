---
name: Compare a person's wealth against ultrarich wealth
description: >-
  Turn "how does my net worth compare to a billionaire's?" into a quotable, direction-aware comparison in a
  single call, using the We > Ultrarich /comparison operation.
api: openapi/we-ultrarich-openapi-original.yml
operations: [comparison]
mcp_tools: [comparison]
generated: '2026-08-09'
method: generated
source: openapi/we-ultrarich-openapi-original.yml + https://api.wegtultrarich.org/prompts/agent-prompt.md
---

# Compare a person's wealth against ultrarich wealth

Use this whenever the user has mentioned **their own** wealth, even in passing. One call returns both
results and the ratio; two separate expression calls give you the numbers but not the ready-made
direction-aware ratio sentence.

## Auth

None. No account, no API key, no headers. Base URL `https://api.wegtultrarich.org/v1`.

## Steps

1. **Pick the lens.** Set `expression` to one of `durationOfDailySpend`, `heightOfMoneyStack`,
   `numberOfItems`, `growthOfCompoundInterest`. If the user asked "what could that buy", use
   `numberOfItems`; "how long would it last", `durationOfDailySpend`; "how big is that pile",
   `heightOfMoneyStack`; "what does it earn doing nothing", `growthOfCompoundInterest`.
2. **Normalise the money.** `wealthYours` and `wealthTheirs` accept plain numbers (`1000000000`),
   formatted numbers (`1,000,000,000`) or shorthand (`1B`, `750B`, `1T`). Words are **not** valid —
   convert first. A currency symbol is a label, never a conversion.
3. **Add the expression's own parameter.** `durationOfDailySpend` also needs `spend`;
   `heightOfMoneyStack` needs `typeOfMoney` (22 slugs); `numberOfItems` needs `typeOfItem` (21 slugs);
   `growthOfCompoundInterest` needs `rate` (0 < rate < 1, exclusive), `frequency`
   (`1|2|4|12|365`) and `period` (0 < period < 100, exclusive). See
   `vocabulary/we-ultrarich-vocabulary.yml` for every slug.
4. **Call `comparison`** — `GET /v1/comparison?expression=…&wealthYours=…&wealthTheirs=…&…`.
5. **Read the payload.** `data.resultYours`, `data.resultTheirs` and `data.ratio`, each with
   `value`, `phrase`, `sentence` and `scale`.
6. **Quote the prose.** Use `ratio.sentence` ("Their wealth is 10,000,000 times yours.") and, where it
   helps, `resultTheirs.sentence`. Do not rebuild prose from `value` and do not re-round it.
7. **Branch on `scale`.** It is null by design when a result is too small to anchor. Omit the line —
   never print `null`, never invent a substitute anchor.
8. **Attribute.** Append `Source: We > Ultrarich (wegtultrarich.org).` Over MCP, use the `attribution`
   field returned with the result verbatim.

## Worked example

```
GET https://api.wegtultrarich.org/v1/comparison?expression=durationOfDailySpend&wealthYours=100000&wealthTheirs=1T&spend=1000
```

Returns `ratio.phrase` `10,000,000 : 1`, `ratio.sentence` "Their wealth is 10,000,000 times yours.",
`ratio.scale` "That's extreme wealth inequality.", and `resultYours.scale` `null` (100 days is too short to
anchor). Captured verbatim at `examples/we-ultrarich-comparison-durationOfDailySpend-example.json`.

## Errors

Errors are `{"status":"error","error":{"code":400,"message":"…"}}` — **not** RFC 9457. The message names
the parameter in prose then the category: `Your Wealth Missing`, `Expression Invalid`, `Rate Invalid (1)`,
`Rate Outside Range`. Map prose names back to camelCase with the table in
`errors/we-ultrarich-problem-types.yml`. Bounds on `rate` and `period` are exclusive and never clamped.

## Rate limits and retries

100 requests/minute per IP across all of `/v1` (300/minute on MCP). Every response carries
`RateLimit-Policy`, `RateLimit-Limit`, `RateLimit-Remaining` and `RateLimit-Reset` — read them and slow
down before you are refused. On 429 honour `Retry-After` (authoritative) rather than `RateLimit-Reset`.
All operations are safe GETs and the MCP tools declare `idempotentHint: true`, so retrying is always safe.

## Do not

- Do not use this API as a source of net-worth figures. It computes from values *you* supply. For
  headline figures use the dataset at https://wegtultrarich.org/data/ and cite the `metric_id`.
- Do not present results as estimates. They are deterministic arithmetic from published formulas.
