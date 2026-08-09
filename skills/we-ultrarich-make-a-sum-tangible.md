---
name: Make a single sum of money tangible
description: >-
  Answer "how much is a billion dollars, really?" with one of the four We > Ultrarich wealth expressions —
  time, physical height, purchasing power, or compound growth — and quote the result correctly.
api: openapi/we-ultrarich-openapi-original.yml
operations: [expressions, durationOfDailySpend, heightOfMoneyStack, numberOfItems, growthOfCompoundInterest]
mcp_tools: [duration_of_daily_spend, height_of_money_stack, number_of_items, growth_of_compound_interest]
generated: '2026-08-09'
method: generated
source: openapi/we-ultrarich-openapi-original.yml + https://api.wegtultrarich.org/prompts/agent-prompt.md
---

# Make a single sum of money tangible

Use this when the user names **one** amount and wants it made concrete. If they mention their own wealth
too, use the `comparison` skill instead — it returns both sides plus the ratio in one call.

## Auth

None. Base URL `https://api.wegtultrarich.org/v1`. All operations are GET.

## Choosing the operation

| The user is asking | Operation | Required parameters |
|---|---|---|
| how long the money would last | `durationOfDailySpend` | `wealth`, `spend` |
| how big the physical pile is | `heightOfMoneyStack` | `wealth`, `typeOfMoney` |
| what it could buy or pay off | `numberOfItems` | `wealth`, `typeOfItem` |
| what it earns untouched | `growthOfCompoundInterest` | `wealth`, `rate`, `frequency`, `period` |

`expressions` lists the available routes if you want to discover them at runtime.

## Steps

1. **Normalise `wealth`** — plain (`1000000000`), formatted (`1,000,000,000`) or shorthand (`1B`, `1T`).
   Words are not valid; convert first.
2. **Pick the slug.** `typeOfMoney` has 22 values across 11 currencies — coins stack far higher than
   bills, so pick coins for maximum contrast; the slug's currency overrides any symbol on `wealth` and
   **no conversion is performed**. `typeOfItem` has 21 values from `fancy_coffee` to `superyacht`; a year
   of minimum-wage salary and a superyacht make very different points, so choose what fits the question.
   Full lists in `vocabulary/we-ultrarich-vocabulary.yml`.
3. **Call the operation** and read `data.value`, `data.unit`, `data.type`, `data.phrase`,
   `data.sentence`, `data.scale`.
4. **Quote `sentence`** in prose, `phrase` for a heading or card, `scale` as the "for scale" line. Do not
   re-round `value` — the prose already applies the project's rounding conventions, and re-rounding
   produces figures that disagree with the sentence beside them.
5. **Branch on `scale`** — null by design when the result is too small to anchor. Omit the line.
6. **Attribute** with `Source: We > Ultrarich (wegtultrarich.org).`

## Worked example

```
GET https://api.wegtultrarich.org/v1/numberOfItems?wealth=250B&typeOfItem=year_of_salary_65k
```

Captured verbatim at `examples/we-ultrarich-numberOfItems-example.json`. Compound-interest bounds are
exclusive and never clamped: `rate=1` returns `Rate Invalid (1)`, `rate=2` returns `Rate Outside Range`;
`period` behaves the same at 0 and 100.

## Errors and limits

See `errors/we-ultrarich-problem-types.yml` (vendor envelope, prose parameter names, six money-value
categories) and `rate-limits/we-ultrarich-rate-limits.yml` (100/min per IP across `/v1`, standard
`RateLimit-*` headers on every response, `Retry-After` authoritative on 429).
