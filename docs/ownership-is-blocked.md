# Ownership: blocked, then unblocked

Kept under its original name because the reasoning is worth more than the
verdict, and because the pause was right until it was measured.

## What was blocked

`wa.tenements.live` — DMIRS layer 3 — carries `holder1`..`holder9`: who holds
live mining ground in Western Australia. Ownership is **overwritten in place**,
so consolidation is invisible after the fact. It is the only source in this
fleet whose entity is an *owner* rather than an *artifact*.

It sat paused because capture stores raw bytes verbatim while the fleet declared
`personal_data: none`, and the note led with:

> 1,446 of 3,604 holders (40%) are named individuals.

## What unblocked it: a denominator

That figure is 40% of **names**. Measured on a 4,000-tenement sample, the split
by **ground** is:

| holder type | share of tenements |
| --- | --- |
| company | **92.5%** |
| individual | 7.5% — median one tenement each |

Forty percent of names, seven percent of ground. The scary framing and the
operative one differ by a denominator, which is the failure this fleet
documents everywhere else and had reproduced in its own pause note.

The largest holders are ASX-listed — Regis Resources, Dynamic Metals, Solstice
Minerals, Dreadnought Exploration. That is the analytical subject, and it has no
privacy dimension at all.

## What the publisher says

WA publishes the register under **CC-BY 4.0**, stated *"Open — this dataset is
available for use by everyone"*, with no fees, no login, **no privacy condition**
and explicit republication rights. A tenement register is a public record kept
so that it can be read.

## How it is handled

- **Parser (v2)** keeps corporate holders verbatim and reduces natural persons
  to a stable digest, so consolidation stays followable and **no derived table
  restates a person's name**. This is pseudonymisation, not anonymisation —
  anyone with the live register can re-identify a digest. The point is that this
  repository does not restate the names itself.
- **Registry** declares `personal_data: parties_only`, which is true: the raw
  archive does contain them.
- **Storage stays `git`.** Object storage was considered and rejected as
  disproportionate *here* — this source adds ~5 MB a month against
  mining-pipeline's ~0 MB/day marginal growth. The fleet will need object
  storage within months for **size** reasons (cloud-footprint first, ~10 weeks),
  and sensitive sources should migrate then rather than building a bucket for
  148 prospectors.

## A bug the unpause exposed

The gid chunk boundaries had gone stale while paused. Live gids run
**7,143,537–7,174,001**; every boundary in the registry sat below that, so seven
of eight endpoints returned zero rows and the eighth tried to pull all 30,465 at
once against a `maxRecordCount` of 10,000.

**The gates caught it** — `must_not_contain: ['exceededTransferLimit":true']`
and `min_bytes: 50000` would have failed every endpoint rather than quietly
storing a third of the register. Re-based to five chunks of ~6,000, roughly 60%
of the cap, leaving room for ~4,000 new grants before the open-ended last chunk
truncates.

**Boundaries drift as tenements are granted.** They are not a set-and-forget
value; the gate is what makes the drift loud.
