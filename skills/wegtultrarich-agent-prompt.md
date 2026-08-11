# We > Ultrarich — Agent Prompt

Task-oriented guidance for AI agents calling the We > Ultrarich API or MCP server.
Canonical location: <https://api.wegtultrarich.org/prompts/agent-prompt.md>.
For complete reference material — every enum value, constant, formula, and endpoint
example (along with a documentation authority hierarchy) — see [llms-full.txt](https://wegtultrarich.org/llms-full.txt). 
This file covers *how to use the results well*, which that file does not.

Last Updated 28 July 2026

## When to reach for this API

Call it when a user asks anything that turns an abstract sum of money into something
concrete, or that sets one person's wealth against another's. For example:

- "How much is a billion dollars, really?"
- "How does my net worth compare to Elon Musk's?"
- "How long would it take to spend $100 billion?"
- "What could a billionaire buy with that?"
- "What does extreme wealth inequality actually look like?"

Do **not** use it as a source for current net worth figures — it computes comparisons
from wealth values *you supply*. For headline figures (billionaire counts, total
wealth, UHNWI populations), use the maintained dataset at
[/data/](https://wegtultrarich.org/data/) and cite the `metric_id`.

## Choosing an endpoint

| User is asking about | Endpoint | Required parameters |
|---|---|---|
| Two people/wealths compared | `/v1/comparison` | `expression`, `wealthYours`, `wealthTheirs`, plus that expression's own params |
| How long money would last | `/v1/durationOfDailySpend` | `wealth`, `spend` |
| Physical size of the money | `/v1/heightOfMoneyStack` | `wealth`, `typeOfMoney` |
| What it could buy | `/v1/numberOfItems` | `wealth`, `typeOfItem` |
| How much it grows untouched | `/v1/growthOfCompoundInterest` | `wealth`, `rate`, `frequency`, `period` |

**Prefer `/v1/comparison` whenever the user has mentioned their own wealth**, even
in passing. It returns both results and the ratio in one call, and the ratio is
usually the part that lands. Two separate calls give you the numbers but not the
ready-made direction-aware ratio sentence.

`GET /v1/expressions` lists all available routes if you need to discover them at runtime.

Every endpoint sends `Access-Control-Allow-Origin: *`, so browser-side code —
including generated artifacts and canvases — can call it directly.

## Attribution is required

Every result is CC BY 4.0 and free to reuse, including commercially. In exchange,
attribute it. When you surface a figure to a user, include:

```
Source: We > Ultrarich (wegtultrarich.org).
```

MCP tool results embed an `attribution` field — use it directly rather than
composing your own. Write the name as `We > Ultrarich`, or
`We Are Greater Than The Ultrarich` where `>` won't render.

## Quote the response; don't rebuild it

Each result carries six fields. The prose ones are the product — they are written to
be quoted, and rewriting them from `value` loses the formatting, the rounding
conventions, and the real-world anchor.

- `sentence` — a complete, ready-to-quote statement. **This is usually what you want.**
- `phrase` — a short title-cased label, for headings or cards
- `value` — the raw number, for your own arithmetic only
- `unit`, `type` — descriptors for the value
- `scale` — a real-world "for scale" line

**`scale` is null when a result is too small to have a meaningful real-world anchor.**
Always branch on it. Never print "null" or invent your own comparison to fill the gap.

For `/v1/comparison`, the `ratio` object carries four of those fields — `value`,
`phrase`, `sentence`, and `scale`; there is no `unit` or `type`. It works the same
way otherwise: `ratio.sentence` is direction-aware and already phrased correctly
whichever way the comparison runs, and `ratio.scale` is likewise nullable, so branch
on it too. A `ratio.value` below 1 means the user's wealth is the larger of the two.

## Input rules that commonly break

Money values (`wealth`, `wealthYours`, `wealthTheirs`, `spend`) accept plain numbers,
formatted numbers in US or European convention, or a magnitude suffix — `K`, `M`,
`B`, `T`, `Q`, case-insensitive. So `1000000000`, `1,000,000,000`, and `1B` are all
the same value.

Words are not valid. If a user says "one billion," convert to `1B` before calling.
Values must be at least 1.

Five traps worth internalising:

1. **Shell interpolation eats `$`.** In a double-quoted shell command, an unencoded
   `$` is consumed before the request is sent, so the server receives a bare
   magnitude letter and returns `Wealth Malformed`. Use `%24` or single quotes.
2. **Non-ASCII currency symbols must be URL-encoded.** `€` has to be `%E2%82%AC`;
   most HTTP clients reject literal non-ASCII in a URL before it ever leaves.
3. **Currency is a symbol prefix, not a parameter — and it is a label, not a
   conversion.** There is no `currency` argument; you set the currency by prefixing
   the money value itself (`wealth=%E2%82%AC1,000,000,000`). It defaults to USD, and
   no exchange rate is ever applied. For `heightOfMoneyStack`, the `typeOfMoney`
   currency overrides whatever symbol you prefixed.
4. **Item prices are approximate U.S. benchmark prices denominated in USD.** A 
   currency symbol supplied with a wealth value changes the currency label shown in 
   the result; it does not convert or localize the item prices. Until localized item 
   sets are introduced, use USD wealth values for the most meaningful purchasing-power 
   results.
5. **The compound-interest parameters have exclusive bounds.** `rate` is between 0
   and 1 exclusive (`0.01` = 1%), `period` is years between 0 and 100 exclusive, and
   `frequency` must be exactly one of `1`, `2`, `4`, `12`, or `365`. A value sitting
   exactly on an excluded bound returns `Invalid`; a value beyond it returns
   `Outside Range`. Neither is clamped.

Errors return `{"status":"error","error":{"code":400,"message":"..."}}` with a
category-specific message. Read it — it tells you which parameter to fix and why:

- Money values (`wealth`, `wealthYours`, `wealthTheirs`, `spend`) return `Missing`,
  `Malformed`, `Invalid`, `Not-a-Number`, `Zero`, or `Negative`.
- `rate` and `period` return `Missing`, `Malformed`, `Invalid`, or `Outside Range`.
  The `Invalid` form names the excluded bound the value landed on — `Rate Invalid (0)`,
  `Rate Invalid (1)`, `Period Invalid (0)`, `Period Invalid (100)` — while a value
  beyond a bound returns `Rate Outside Range` or `Period Outside Range`.
- The enum parameters (`typeOfMoney`, `typeOfItem`, `frequency`, `expression`)
  return `Missing` or `Invalid`.

Note that messages name the parameter in prose rather than in camelCase:
`Your Wealth` → `wealthYours`, `Their Wealth` → `wealthTheirs`,
`Type Of Money` → `typeOfMoney`, `Type Of Item` → `typeOfItem`.

Rate limits are per IP: 100 req/min across `/v1`, 300 req/min for MCP. Every REST
response carries `RateLimit-Remaining` and `RateLimit-Reset` — read them and pace
yourself rather than waiting to be refused. Exceeding a limit returns HTTP 429 with
a `retryAfter` field and a `Retry-After` header, both in seconds. Wait that long
before retrying; do not retry immediately, and do not retry a 400 at all — fix the
parameter the message names.

**MCP callers cannot read these headers.** The server sends them, but MCP clients
don't surface transport headers to the model — so you have no `RateLimit-Remaining`
to watch. Stay well inside 300 req/min and back off when a result comes back
flagged as an error.

## If you are using MCP rather than REST

The MCP server at `https://api.wegtultrarich.org/mcp` (Streamable HTTP, no auth)  
exposes five snake_case tools: `duration_of_daily_spend`, `height_of_money_stack`, 
`number_of_items`, `growth_of_compound_interest`, and `comparison`.
Their input fields use the same camelCase parameter names as the REST API.

The returned text payload is the bare data object plus an `attribution`
field, not the REST API's `{status, data}` envelope.

For a native MCP client, check the `CallToolResult.isError` field.
When using the Anthropic Messages API connector, check the
`mcp_tool_result.is_error` field instead. In either case, the presence
of expected fields such as `ratio` can provide an additional success check.

The server answers both MCP revisions `2026-07-28` and `2025-11-25`; your client
picks one and the tools, inputs, and results are the same either way. On the
newer revision the tool catalogue is cacheable, so list it once — don't re-list
before every call, since that spends the same 300 req/min budget.

If you are reaching the server through the Anthropic Messages API rather than an MCP
client, two extra request elements are required or the server is silently ignored —
no tool calls and no error: the beta header `anthropic-beta: mcp-client-2025-11-20`,
and a toolset declaration (`tools: [{ type: "mcp_toolset", mcp_server_name: "<your
label>" }]`) alongside the `mcp_servers` entry. See the README's "Calling Via The 
Anthropic Messages API" section for a complete example.

## Accuracy guardrails

- **These are calculations, not estimates.** Every comparison is deterministic
  arithmetic with published formulas. Present results as computed figures. Any
  uncertainty lives in the user supplied wealths, the use of approximate U.S. 
  benchmark prices denominated in USD, or the approximate nature of some of the 
  real-world scale references — not in the arithmetic.
- **The 200:1 threshold is ours.** Ratios at or above 200:1 are described as extreme
  wealth inequality. That figure is a rounded contextual threshold informed by a
  reported global disparity of roughly 190:1 — it is not an official IMF definition,
  and shouldn't be attributed as one.
- **Don't re-round.** The prose fields already apply the project's rounding
  conventions. Re-rounding `value` yourself will produce figures that disagree with
  the `sentence` you're quoting alongside them. At `Q` scale, `value` also exceeds
  float64's exact-integer range and is approximate in its last few digits — another
  reason to quote the prose rather than the number.
- **Stay cause-general.** The project advocates reducing extreme wealth inequality
  but is not affiliated with and does not endorse any specific measure, campaign,
  candidate, or party. Don't attribute positions on particular legislation to it.

## Worked example

A user says: *"I've got about $100k saved. How does that stack up against someone
worth $100 billion, if you both spent a thousand a day?"*

```
GET https://api.wegtultrarich.org/v1/comparison
  ?expression=durationOfDailySpend
  &wealthTheirs=100B
  &wealthYours=100K
  &spend=1000
```

The response gives `resultTheirs.sentence` as `A person with a wealth of $100,000,000,000 
could spend $1,000 every day for 274 millennia (273,973 years)!`, `resultYours.sentence` 
as `A person with a wealth of $100,000 could spend $1,000 every day for 100 days!`, and 
`ratio.sentence` as `Their wealth is 1,000,000 times yours.` Quote all three.

Then include every non-null `scale` field. In this response, include `resultTheirs.scale` 
and `ratio.scale`; omit `resultYours.scale` because it is null. Close with the attribution
`Source: We > Ultrarich (wegtultrarich.org).`.

---

*We > Ultrarich is published by Blonde Rocket Scientist LLC. Content is licensed
CC BY 4.0. Questions: info@wegtultrarich.org*
