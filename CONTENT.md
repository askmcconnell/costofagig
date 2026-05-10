# CONTEXT.md — For AI Assistants

## What This Project Is

**Jim McConnell's Annual "Cost of a Gig" Fun Post** is a 47-year personal dataset tracking the retail cost of 1 gigabyte of removable storage media, published annually each October on LinkedIn and Facebook. Jim started his first technology job in October 1982 at The Software Store on Fowler Ave in Tampa, FL, selling Elephant brand DS/DD 5.25" diskettes at $19.95 for a 10-pack (360KB each = ~$5,541/GB). Every year since he has done a non-scientific retail search to find the current cost of removable storage and compared it to that 1982 baseline.

This repository is the **golden source dataset** behind that tradition, compiled in May 2026 in collaboration with Claude (Anthropic) to prepare for the October 2026 post.

---

## Repository Structure

| File | Purpose |
|---|---|
| `README.md` | Full data tables — annual posts 2009–2025, historical catalog data 1977–2009 |
| `data.json` | Structured JSON of all data points — use this for charting/programmatic access |
| `SOURCES.md` | Full citation list — Radio Shack catalogs, Computer Shopper, Maximum PC, Fry's ads |
| `CONTEXT.md` | This file — AI assistant orientation |

---

## Key Facts

- **1982 baseline:** $5,541.67/GB (Elephant DS/DD, $19.95/10-pack, 360KB/disk)
- **2025 best price:** $0.025/GB (30TB Portable HDD)
- **Total improvement:** ~361,000× cheaper in 43 years
- **1977 cassette baseline:** $9,034/GB (Radio Shack Realistic Low-Noise C-60, catalog verified)
- **DS/DD floppy today (2025):** $6,931/GB — more expensive than 1982 due to NOS scarcity

## Physical Scale (great for infographics)
- 1GB in 1977 cassettes = 5,682 tapes = ~237 feet tall
- 1GB in 1982 floppies = 2,777 diskettes = ~30 feet tall
- 1TB in 2025 = 1 microSD card = size of a fingernail

---

## Data Coverage

| Period | Source |
|---|---|
| 1977–2009 | Radio Shack catalogs, Computer Shopper, Maximum PC, Fry's ads |
| 2009–2025 | Jim's personal LinkedIn/Facebook annual posts |
| 2015–2025 | Most complete — multiple media types per year with YoY % |

**Key historical data points:**
- 1977: Cassette $9,034/GB
- 1981: Flip/Floppy $11,364/GB
- 1982: DS/DD Elephant $5,541/GB ← the origin
- 1984: Radio Shack SS/DD $22,699/GB (price spike)
- 1996: CD-R debuts at $12.15/GB — begins the optical era
- 1998: CD-R drops to $2.14/GB
- 2000: Format war — CD-R, Zip, SuperDisk, floppy all competing
- 2001: First USB thumb drive (DiskOnKey 128MB) at $1,172/GB
- 2003: USB flash $281/GB
- 2006: DVD $0.17/GB, USB still $78/GB
- 2009: DVD $0.021/GB, USB $13.50/GB, HDD $0.068/GB

---

## October 2026 Post — Planned Additions

1. **Cassette row** added to annual table (~$9,034/GB, 1977 Radio Shack catalog verified)
2. **Physical scale infographic** — cassette tower (237ft) vs floppy stack (30ft) vs microSD fingernail
3. **Format introduction callout bubbles** on the price chart
4. **LinkedIn/Facebook post narrative** draft

---

## Website Integration Notes

- The annual post is published on **LinkedIn and Facebook** each October
- The post uses a **table format** showing media type, $/GB, and YoY % change
- Tone is **friendly, non-technical, humor-forward** — "non-scientific retail search"
- The **DS/DD floppy row** is always included as a running joke/historical anchor
- Signature phrases: *"Annual Cost Per Gig Fun Post"*, *"non-scientific retail search"*
- The **Elephant brand yellow box** with "Never Forget" logo is the visual brand anchor
- A **ChatGPT-generated scale image** exists showing cassette tower vs floppy stack vs building (needs correction — cassette stack should be 237ft not 74ft)

---

## Data JSON Structure

```json
{
  "baseline": { ... },
  "physical_scale": { ... },
  "annual_posts": [ { "year": 2025, "data": [...] } ],
  "historical_catalog_data": [ { "year": 1977, ... } ],
  "cassette_technical": { ... },
  "todo_2026": [ ... ]
}
```

---

## Still Being Researched

- Personal posts from 2010, 2011, 2013, 2014 (LinkedIn/Facebook search ongoing)
- Additional catalog data points for gap years

---

## Contact / Owner

**Jim McConnell** — github.com/askmcconnell
Annual post published every October since ~2009 (tradition started 1982)
