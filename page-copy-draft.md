# Cost of a Gig — Page Copy Draft

*For review before pasting into the WordPress page at `/costofagig/`. One quick fix first: the live page title has a typo — "historcial" should be "historical."*

---

## 1. Hero / Intro

> **Cost of a Gig**
> A 49-year, non-scientific retail history of what it costs to store one gigabyte of data.

In October 1982, I started my first job in technology — selling boxes of Elephant Brand DS/DD 5.25" diskettes at The Software Store on Fowler Ave in Tampa, FL. A 10-pack ran $19.95. Each disk held 360KB. Do the math and that's **$5,541.67 per gigabyte.**

Every year since, I've done a completely non-scientific retail search — Amazon, Google, whatever's on the shelf — to see what a gigabyte costs today. This page is the running record.

---

## 2. This Year's Headline (2026)

**For the first time in this dataset's history, storage got more expensive almost across the board.**

Of the 13 items priced so far this year:
- **9 rose year-over-year** — most by 60% to nearly 300%
- **1 dropped** (32TB bare HDD, down 40%)
- **1 held essentially flat** (the DS/DD floppy — no surprise there)
- **2 are new entries** with no prior-year comparison yet

For 40+ years, the rule was simple: storage gets cheaper, no matter what else is happening in the economy. This year broke that rule.

**The bookend stat:** the 1977 Radio Shack C-60 cassette tape cost $9,034/GB. The same style of cassette, bought on Amazon today, costs **$32,073.86/GB** — up 255% from where this whole tradition started, and up 33% from just last year.

*(Full breakdown in the table below.)*

---

## 3. Interactive Chart

*[Embed `chart-embed.html` here as a Custom HTML block — see separate file]*

Log-scale chart of the cheapest available storage each year, plotted against two "anchor" formats that never really got cheaper: the DS/DD floppy (1982 baseline) and the C-60 cassette (1977 bookend). The chart pulls live from the [public dataset on GitHub](https://github.com/askmcconnell/costofagig), so it updates automatically every October.

---

## 4. Physical Scale — 1 Gigabyte, Then and Now

*(Corrected graphic still in progress — placeholder text below; swap in the SVG/image once it's ready.)*

| Format | Units needed for 1GB | Stack height |
|---|---|---|
| C-60 Cassette (1977) | 5,682 cassettes | ~237 feet |
| DS/DD Floppy (1982) | 2,777 diskettes | ~30 feet |
| microSD card (2025+) | 1 card | Size of a fingernail |

*Note: the existing scale illustration shows the cassette tower at 74 feet — that's wrong, it should be 237 feet. Needs a corrected version before this section goes live with a graphic.*

---

## 5. The Full 2026 Table

*Sorted cheapest to most expensive per GB.*

| Media | $/GB (2026) | YoY vs. 2025 |
|---|---|---|
| 32TB Bare HDD (Seagate Skyhawk AI) | $0.0362 | −40% |
| 30TB Portable HDD (Glyph) | $0.0666 | +163% |
| 1TB Thumb Drive (Generic) | $0.10 | +61% |
| 1TB Thumb Drive (Name Brand) | $0.15 | +97% |
| 2TB microSD (Lexar) | $0.1766 | +108% |
| 512GB microSD | $0.2324 | +297% |
| 2TB SD Card, full-size (SanDisk) | $0.275 | *new* |
| 30TB Portable SSD (Glyph NVMe) | $0.36 | +140% |
| CFExpress Type B 4TB | $0.3985 | +77% |
| 122.88TB SSD (Samsung) | $0.4639 | +277% |
| 8TB CineMag 5e | $4.0017 | −35% |
| DS/DD Floppy | $6,928.61 | −0.03% |
| C-60 Cassette (Qty 2) | $32,073.86 | +33% |

---

## 6. Methodology & Sources

Prices are retail snapshots from a non-scientific search each fall — mostly Amazon, occasionally a specialty retailer for professional-grade media. Not necessarily the lowest price available anywhere, just a representative real-world number. Full sourcing, historical catalog data (Radio Shack, Computer Shopper, Maximum PC), and the complete year-by-year dataset back to 1977 are public on GitHub:

**[github.com/askmcconnell/costofagig](https://github.com/askmcconnell/costofagig)**

---

## Open items before this is "final"
- [ ] Fix page title typo ("historcial" → "historical")
- [ ] Corrected physical-scale graphic (237ft, not 74ft)
- [ ] Price for SanDisk's newly announced 256TB SSD, if you want to add it before publishing
