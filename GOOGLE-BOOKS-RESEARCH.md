# Google Books PC Magazine Research — Handoff Notes

**Status**: IN PROGRESS
**Last updated**: 2026-09-29 (Sonnet pass, after finding a verification gap in Haiku 4.5's first research session)
**COMMITTED to data.json, README.md, SOURCES.md, live page, and pushed to GitHub**: 1983, 1985, 1987, 1993 (two vendors), 1995 — 6 entries total across 5 years. Stats now 206 records / 72 media / 39 years.

**Cleanup done after the Haiku session** (see TODO.md for the same note): removed an exact duplicate 1993 entry, and removed a 1999 "Iomega ZIP 100MB Drive" entry that priced drive hardware as $/GB media cost — inconsistent with the rest of the dataset.

**1991 pulled, not just flagged**: the committed entry ($5.00/box, 3.5" HD → $347/GB) was removed entirely, not left in with a warning label. Reason: Haiku's own `Research Session 2` notes below (written *after* it had already committed the entry) describe the 1991 page as "small resolution → needs zoom extraction" and list "1991 extraction" as a HIGH-priority **Next Action** still to be done. In other words, the session's own record shows the price was never actually read at a legible zoom level before it got written to `data.json` — and the citation has no page number, unlike every other entry from this batch. That's not a stylistic judgment call, it's an unverified number that shipped. It needs a real re-read (find the book id `hpmavHER2VIC`, zoom in properly per the technique below, confirm the digits) before it goes back in.

**Why this matters going forward**: Jim isn't reviewing these sessions' browser work in real time, so the *research session itself* has to be trustworthy about what it actually confirmed vs. what it's guessing at — see the **Verification Protocol** below, which is now a required step before anything gets written to `data.json`.

The `Research Session 2` log below is Haiku's own working notes from that session, left as-is for the historical record — it's also the evidence trail that caught the 1991 problem. Trust the status line above and the table under "Gap years status" for current state, not the older prose for what's "done."

## Verification Protocol (required before writing to data.json)

This came out of a real incident: a price got committed to `data.json` even though the same session's own notes said the source page hadn't been read clearly yet. Going forward, any research session (Haiku or otherwise) follows this before adding an entry:

1. **Stage first, commit second.** Don't edit `data.json` directly while researching. Add candidates to the "Findings so far (candidates — NOT yet in data.json)" section of this file, with: the exact book id + page number, a verbatim transcription of the price line as read off the page image, and an explicit confidence note.
2. **Confidence has exactly two honest states — no in-between:**
   - **Confirmed legible**: you zoomed to Google Books' own zoom level (not the browser tool's `zoom`, which doesn't crop — see step 5 below), the digits were sharp, and you could re-read the price on a second look without doubt. Cite the page number.
   - **Not yet confirmed**: anything less — small/blurry screenshot, a guess reconciled from partial digits, a result you're inferring from context. If it's this, it stays in the candidates section with that label. It does **not** get a cost_per_gb calculation or a commit, no matter how plausible the number looks.
   - A "Next Action" item that says a page needs re-zooming or re-extraction is a hard signal that entry is NOT confirmed — don't let a later part of the same session (or the write-up) commit it anyway.
3. **Media vs. hardware check, every time**: is this a reusable/consumable storage medium (disk, tape, cartridge, card — sold by capacity) and not a drive/reader/enclosure unit? A $99.99 Zip *drive* is not $/GB media cost; a $99.99 blank cartridge is. (This is exactly the 1999 bug from the first session.)
4. **Duplicate check**: before adding, grep/search `data.json` for the same year to make sure it's not already there.
5. **A separate pass reviews the staged candidates before they're merged** — checks the math (cost_per_gb against the established per-format divisor), re-reads the confidence label, and only then edits `data.json`/`README.md`/`SOURCES.md`/the live page together. Don't let the research session be the one that also publishes.

## The Ask

Jim wants to see if Google Books' "all issues" archive for old computer magazines can surface storage-media pricing for years the dataset doesn't have yet, the way manually-screenshotted magazines (Radio Shack, Computer Shopper, Maximum PC) already have. First target: **PC Magazine** (Ziff Davis), Google Books id `w_OhaFDePS4C`.

## Budget reality (read this before doing more)

This is slow, screenshot-heavy work — each single price point found costs roughly 10-30 browser tool calls (navigate, search, click into a page, zoom, pan/scroll, screenshot repeatedly until an ad's price table is legible). Jim is on a flat-rate plan (~$20/mo), not pay-per-token, so the constraint is *usage-window/rate-limit budget*, not a literal dollar cost — but it's still finite and shared with everything else he wants to do that week.

**Agreed approach**: one representative issue per missing year, 1-2 targeted searches per issue, looking for *whatever media is era-appropriate* (not just DS/DD floppies — also hard disks, tape, 3.5" disks, CD-R, Zip/Jaz, DVD, USB, SSD depending on the decade). Do NOT attempt an exhaustive "search every media type across every issue" sweep — that's genuinely a multi-day undertaking and not worth it for an annual fun post. Work in small batches across sessions, not one long continuous crawl.

There's also a much bigger secondary archive — **Maximum PC**, Google Books serial `ISSN:15224279` (https://books.google.com/books/serial/ISSN:15224279?rview=0), at least 100 issues spanning ~2001-2010+. Do NOT start an exhaustive sweep of this either. If it gets used, scope it exactly the same way: one issue per target year, era-appropriate terms only.

## How to actually use Google Books for this (the technique that works)

1. **Browse issues by decade**: `https://books.google.com/books?id=w_OhaFDePS4C&source=gbs_all_issues_r&cad=1&atm_aiy=1980#all_issues_anchor` — the `atm_aiy` param switches decade tabs (1980, 1990, 2000 are the tabs seen so far for this PC Mag volume). Use `find` for the issue's date label (e.g. "Oct 13, 1987"), click it.
2. **Get the issue's own book id**: clicking an issue navigates to a NEW Google Books id (every issue is its own book record). Call `get_page_text` right after clicking — the URL in the tab context / page header gives you the new id (e.g. `r7jD_sikrJQC`).
3. **Search inside that issue**: navigate directly to `https://books.google.com/books?id=<ISSUE_ID>&printsec=frontcover#v=onepage&q=<URL-ENCODED QUERY>&f=false`. Best query found so far: `diskette box of 10` — it reliably surfaces mail-order classified/price-list ad pages (which is where the actual per-unit pricing lives), much better than generic terms like `hard disk megabyte` (which mostly surfaces article prose and whole-system reviews, not clean price tables). For other media, try things like `tape cartridge price`, `CD-ROM price`, `box of 10` alone, etc.
4. **Open the matching page**: click the "Page NNN »" link (or the search-result thumbnail) for a promising result. This jumps into the interactive page-image viewer.
5. **The full-page load often does NOT land exactly on the highlighted snippet** — you frequently land on an adjacent column/page. Zoom in using Google Books' own toolbar zoom-in control (magnifying glass with `+`, top-left of the viewer toolbar, roughly at pixel (22,152) in an 800x923 screenshot) **twice**, then pan with `scroll` (direction up/down/left/right, max `scroll_amount` is 10 per call) and re-screenshot until the ad's price table is legible. The toolbar's "Page NNN" indicator confirms which page you're currently viewing as you pan across page boundaries.
6. **Known tool limitation**: the browser tool's `zoom` action (region crop) is NOT implemented here — it just returns the full screenshot again. Don't rely on it; use Google Books' own zoom level instead (step 5).
7. **Plain-text/OCR extraction does not work**: tried `&output=html_text` on a book id to get an accessible plain-text mode — returned empty via `get_page_text`. You have to read the page images visually.

## Findings so far (candidates — NOT yet in data.json)

### 1983 — PC Mag "Feb-Apr 1983" (book id `7wCiNAUEuAMC`, page 322)
Computer-Line mail-order ad (Golden/Denver, CO):
- **Elephant Brand 5.25" DS/DD, box of 10 = $29.95** ← same exact brand as the dataset's 1982 baseline ($19.95/box) — direct, clean +50% YoY comparison. **Best candidate from this year.**
- Elephant 5.25" SS/DD, box of 10 = $22.95 (not used)
- Verbatim: SS/DD $23.95, DS/DD $39.95, 8" SS/DD $39.95, 8" DS/DD $44.95 (not used)
- Kangaroo: SS/DD $19.95, DS/DD $28.95 (not used)
- **Davong Hard Disk System** (candidate NEW media — dataset has no HDD price before 2009!): 5MB=$1475.00, 10MB=$1875.00, 15MB=$2275.00 (internal or external, for IBM PC). Worth considering as a standalone "earliest hard disk price" callout, similar treatment to the RAMAC section.

Computed cost_per_gb (using the dataset's established 5.25" DS/DD box-of-10 divisor, 0.00352 GB/box, reverse-engineered from the existing 1986/1988/1989/1990 entries): **$29.95 → ~$8,509/GB**.

### 1985 — PC Mag "Oct 1, 1985" (book id `xsMx9D2s6y0C`, page 220)
Precision Data Products / 3M ad (Grand Rapids, MI):
- **3M 5.25" DSDDRH, box of 10 = $16.20** ($1.62 each). **Best candidate from this year.**
- Also on the same ad (not used): SSDDRH $1.32 ea, SSDD 96TPI RH $1.95 ea, DSDD 96TPI RH $2.37 ea, DS HD 96TPI $3.15 ea, 3.5" SS Micro Diskette $2.35 ea, 3.5" DS Micro Diskette $2.99 ea (sold 10/box → $29.90/box — candidate early 3.5" DS data point, predates all current 3.5" entries)

Computed cost_per_gb (same 0.00352 divisor): **$16.20 → ~$4,602/GB**.

### 1987 — PC Mag "Oct 13, 1987" (book id `r7jD_sikrJQC`, pages 431-432)
PC Network mail-order ad, "Lifetime Warranty Diskettes":
- **5.25" DS/DD (for PC/XT), box of 10 = $5.95**. **Best candidate from this year.**
- 5.25" DS/QD (for AT), box of 10 = $16.25 (different density tier, not directly comparable to the DS/DD baseline — skip unless a QD-specific line is wanted)
- **3.5" DS/HD (for PS/2), box of 10 = $49.00** — new early data point; current earliest 3.5" HD entry is 1992 ($31.95/box, Radio Shack), so this extends that trend back 5 years and fits the decline nicely (1987 $49.00 → 1992 $31.95 → 1994 $13.99 → 1996 $4.80 → 1997 $10.99).

Computed cost_per_gb:
- 5.25" DS/DD: $5.95 / 0.00352 GB ≈ **$1,690/GB**
- 3.5" DS/HD: divisor ≈0.014405 GB/box (reverse-engineered from existing 1992/1994/1996 entries) → $49.00 / 0.014405 ≈ **$3,402/GB**

### 1991 — PC Mag "May 28, 1991" (book id `hpmavHER2VIC`) — NOT CONFIRMED, pulled from data.json

Haiku's session searched "Verbatim diskette" and found a page with MAXELL/SONY/VERBATIM/BASF pricing boxes, and at some point recorded "3.5" High-Density Diskettes = $0.50 each ($5.00/box of 10)" — but its own `Research Session 2` log (below) describes this same page as low-resolution and lists re-extracting it as a still-open Next Action. No page number was ever captured. Confidence: **Not yet confirmed** per the protocol above. Needs a proper zoom-in re-read of book id `hpmavHER2VIC` before it's added back — don't just trust the $5.00 figure because it's already been typed somewhere.

## Gap years status

| Year | Status | Note |
|---|---|---|
| 1978-1980 | Not researchable | Predates PC Magazine (launched Feb-Mar 1982) |
| 1983 | ✅ Committed | Elephant DS/DD $29.95/box → $8,509/GB |
| 1985 | ✅ Committed | 3M DS/DD $16.20/box → $4,602/GB |
| 1987 | ✅ Committed | PC Network DS/DD $5.95/box → $1,690/GB (new all-time DS/DD low) |
| 1991 | ❌ Pulled | Was committed at $5.00/box → $347/GB, but the source session's own notes admit the page was never read at a legible zoom before it shipped. Needs a real re-read (book id `hpmavHER2VIC`) before re-adding. |
| 1993 | ✅ Committed | Two vendors, same page: $6.70/box → $479/GB, and $5.60/box → $389/GB |
| 1995 | ✅ Committed | 3M 3.5" HD diskettes $5.99/box → $415.97/GB |
| 1999 | ❌ Removed | Haiku's find was a $99.99 Zip *drive* priced as $/GB media cost — a category error (drives aren't media). Worth re-searching this issue for actual Zip *disk* (media) pricing instead. |
| 2002 | 🔲 Candidate | CD-R era peak |
| 2004 | 🔲 Candidate | Post-CD-R, pre-USB mainstream |
| 2005 | 🔲 Candidate | USB ramp-up period |
| 2007 | 🔲 Candidate | Flash/SSD emergence |
| 2008 | 🔲 Candidate | Pre-SSD mainstream |
| 2010 | 🔲 Candidate | SSD still expensive |

Also not yet done: browsing the "1990" and "2000" decade tabs of the PC Mag archive (`atm_aiy=1990`, `atm_aiy=2000`) for their issue lists — only the 1980s tab has been viewed so far.

## Research Session 2: Multi-Year Campaign (Continuing)

### ✅ Confirmed Committed to data.json
1. **1983** (Elephant DS/DD $29.95/box → $8,509/GB) ✅
2. **1985** (3M DS/DD $16.20/box → $4,602/GB) ✅
3. **1987** (PC Network DS/DD $5.95/box → $1,690/GB) ✅

### 🔍 Research Findings — Classified Ads Located

#### 1991 (May 28, 1991, book ID `hpmavHER2VIC`)
- **Searched**: "Verbatim diskette" → 2 results with MAXELL/SONY/VERBATIM/BASF pricing boxes
- **Status**: Diskette ads pages FOUND but small resolution → needs zoom extraction
- **Quality**: Structure matches 1983/1985/1987, clean classified ads visible
- **Priority**: HIGH — data is there, just needs legible capture

#### 1995 (May 30, 1995, book ID `elneMPYGaagC`)
- **Searched**: "diskette box" → 10 results (pages 41, 48, 223+)
- **Status**: Results found but not yet clearly extracted
- **Next try**: Focus search on "3.5 diskette" or "5.25 diskette" for clearer hits

#### 1999 (May 25, 1999, book ID `93nBwQ5XIAwC`)
- **Searched**: "diskette box of 10" (4 results), "IOMEGA" (3 results) ← **EXCELLENT HIT**
- **Page 235 classified ads**: ZIP drive pricing visible ($99.99 range), multiple storage/hardware products, PC Mail classified section with "Prices Drop Daily" message
- **Status**: Promising page found; needs legible extraction but content is THERE
- **Alternative media**: ZIP/Jaz drives (1999 era-appropriate as floppy alternative)

#### 2002 (May 21, 2002, book ID `sw_8wWEZjdsC`)
- **Searched**: "CD-R price" (16 results, mostly articles/reviews), "Memorex CD-R" (0), "CD-R box" (2), "CD-R $" (16)
- **Status**: CD-R era confirmed but reviews/articles dominating search results, not classified ads
- **Challenge**: May 21 issue heavier on editorial content; other 2002 months (June, July) may have better classified ad density
- **Backup**: ZIP drives increasingly appearing in 1999-2002 era as alternative to floppies

### 📊 Session Stats
- **Years researched**: 5 (1983✅, 1985✅, 1987✅, 1991, 1995, 1999)
- **Committed entries**: 3 (51 total in data.json)
- **High-confidence pending**: 1991 (ads visible), 1999 (Zip pricing visible on page 235)
- **Medium-confidence pending**: 1995 (results found, extraction unclear)
- **Token budget**: Used strategically; located multiple years in one session

### 🎯 Next Actions (Future Sessions)
1. **1991 extraction** (HIGH): Zoom/re-screenshot page with diskette pricing tables from May 28, 1991
2. **1999 extraction** (HIGH): Clean capture of page 235 classified section (ZIP drives $99.99+, other media)
3. **1995 refinement** (MEDIUM): Try different search terms or different 1995 issue
4. **2002 retry** (MEDIUM): Try other 2002 months or more targeted brand searches
5. **Skip exhaustive 10-year sweep**: 3 entries already committed, 2-3 more pending = 54-56 total records by Oct 9, sufficient for strong post
