# Data shape

*Generated 2026-09-15T13:15:04Z by `wss schema` from the derived rows. Do not hand-edit — regenerate after any derive.*

**You should not need to download anything to read this.**

- **317,379 observations** across 1 partition(s), in **2 series**
  - `wa.minedex.sites` — 195,517 rows, **48414 entities**
  - `wa.tenements.live` — 121,862 rows, **30483 entities**
- Raw: 28 file(s), 13,403,453 bytes on disk, 4 capture date(s), 2026-09-03 → 2026-09-08

## Sources

| source | cadence | endpoints | storage | personal data | licence |
| --- | --- | ---: | --- | --- | --- |
| `wa.minedex.sites` | monthly | 12 | git | none | Creative Commons Attribution 4.0 (WA SLIP public services);  |
| `wa.tenements.live` | monthly | 6 | git | parties_only | Creative Commons Attribution 4.0 (WA SLIP public services);  |

## Columns

```
series_id, entity_id, observed_at, captured_at, metric, value, unit, source_id, raw_ref, parser_version
```

`entity_id` looks like: **wa.minedex.sites** `site:wa:S0000001`, `site:wa:S0000002`, `site:wa:S0000005`; **wa.tenements.live** `tenement:wa:AG 7000003`, `tenement:wa:AG 7000004`, `tenement:wa:AG 7000005`

## Metrics

| metric | series | rows | entities | type | unit | distinct | range / samples |
| --- | --- | ---: | ---: | --- | --- | ---: | --- |
| `area` | wa.tenements.live | 60,931 | 30483 | number | HA. | 15089 | `0.01` … `702261.0` |
| `commodity` | wa.minedex.sites | 65,167 | 48406 | text |  | 49 | `ALUNITE`, `ANDALUSITE - KYANITE - S`, `ANTIMONY` |
| `holder` | wa.tenements.live | 60,931 | 30483 | text |  | 3607 | `1 BRUNSWICK BAY SE51 PER`, `1 DARWIN SD52 PERTH PTY `, `1 HAMERSLEY RANGE SF50 P` |
| `site_type` | wa.minedex.sites | 65,175 | 48414 | text |  | 9 | `Deposit`, `Geological Observation`, `Infrastructure` |
| `stage` | wa.minedex.sites | 65,175 | 48414 | text |  | 6 | `Care and Maintenance`, `Operating`, `Proposed` |

## Partitions

- `derived/observations/2026-09.csv.gz`
