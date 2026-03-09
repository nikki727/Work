# AI Mandate Playbook — Project Handoff
**For:** Colleague picking this up in Claude Code  
**Project owner:** Nigel (content & marketing, Numeric)  
**Last updated:** March 9, 2026  
**Status:** Active build — all individual assets complete, hub integration pending

---

## What This Is

The **AI Mandate Playbook** is a content hub campaign targeting Controllers, VPs of Finance, and Accounting Managers who are receiving top-down AI directives from CFOs and boards. The central tension: high expectations, zero margin for error.

The hub is not a lead-gen gate. It's a **fully open, genuinely useful resource** — designed so that finance professionals share it organically because it helps them do their jobs. No content gating. The diagnostic orients; it doesn't gate.

Success looks like: a Controller posting on LinkedIn saying "Numeric's AI Mandate Playbook actually helped me do my job better."

---

## Key Stakeholders

| Person | Role | Relevance |
|--------|------|-----------|
| **Tierney** | Senior internal / creative director | Established original strategic direction; owns a five-phase implementation methodology that anchors the entire hub structure |
| **Nigel** | Content & marketing, Numeric | Project owner; your counterpart |
| **Tom & Cindy** | CrossCountry Consulting | External interview subjects; strong on failure modes, steering committees, SOP discipline |
| **Francisco & Kenny** | Abridge | External interview subjects; proof point for organic AI adoption; Kenny Kha is the "accounting engineer" archetype |
| **David Fuhriman** | CFO, Jewish Federation of San Diego | Author of *Infinite Work*; his Five Foundations framework maps to Tierney's five phases (complementary, not competing) |
| **Drew Armanino & Dean Quiambao** | Armanino (consulting) | External interview subjects; strong on build vs. buy vendor evaluation, demo skepticism, AI-native vs. AI-layered |

---

## The Five-Phase Framework (Tierney)

The hub is structured around Tierney's five phases. Every asset is phase-tagged.

1. **Assess** — Understand your mandate, your gaps, your data reality
2. **Prioritize** — Pick the right first use cases; don't automate your worst processes
3. **Build** — Pilots, SOPs, hiring for accounting engineers
4. **Scale** — Governance, steering committees, measurement
5. **Govern** — Auditability, defensibility, long-term ownership

David Fuhriman's Five Foundations (from *Infinite Work*) address **organizational readiness** — they map across all five phases and are complementary, not competing with Tierney's sequencing.

---

## Design Principles

- **Fully open** — no content gating of any kind
- **External resources throughout** — 3–4 per phase; signals helpfulness, not self-promotion
- **Organic sharing over engineered virality** — the shareable artifact mechanic from AirOps was explicitly rejected
- **The diagnostic orients** — it tells you where you are in the journey, not whether you can access content
- **Design reference:** AirOps Marketype quiz (entry experience) + BDR Onboarding Hub (actionability). Dark, editorial, finance-grade.

---

## What's Been Built

All files were output as standalone HTML, DOCX, XLSX, and PPTX. The integration work (stitching into a unified site) is the next major workstream — this is where Claude Code comes in.

### Interactive Tools (HTML)

| Asset | File | Status | Notes |
|-------|------|--------|-------|
| **AI Mandate Hub** | `ai-mandate-hub.html` (or similar) | ✅ Complete | Main hub prototype — hero, five-phase journey map, phase modals, resource library |
| **AI Mandate Diagnostic** | `ai-mandate-diagnostic.html` | ✅ Complete | 5-question situational diagnostic; drops user into the right phase; does NOT gate content |
| **Infinite Work Diagnostic** | `ai-mandate-diagnostic.html` (separate) | ✅ Complete | David's Five Foundations assessment; scores organizational readiness |
| **Build vs. Buy Calculator** | `build-vs-buy-calculator.html` | ✅ Complete | Weighted 5-factor scoring tool; spectrum needle moves toward Buy / Build on Platform / Build |
| **API Library** | separate HTML | ✅ Complete | Visual map of accounting tool integrations + rationale per API |
| **Hackathon / Implementation Scheduler** | HTML + XLSX | ✅ Complete | Hub tool + downloadable Weekly Automation Log (4-sheet XLSX) |

### Downloadable Templates

| Asset | File | Status | Notes |
|-------|------|--------|-------|
| **CFO Defense Deck** | `.pptx` (multi-section) | ✅ Complete | 30-slide deck across 6 files; needs merge into single deck |
| **Build vs. Buy Worksheet** | `build-vs-buy-worksheet.docx` | ✅ Complete | 1-page fillable; same 5 factors as calculator; manual scoring + spectrum |
| **SOP Documentation Starter** | `.docx` | ✅ Complete | 7-section template grounded in CrossCountry + David Fuhriman transcripts |
| **Hiring Exercises for Accounting Engineers** | `.xlsx` + candidate brief HTML | ✅ Complete | Messy payroll register exercise; based on Francisco/Kenny interview |
| **Infinite Work Mapping Worksheet** | HTML/DOCX | ✅ Complete | Maps David's Five Foundations to Tierney's phases |

### Still Outstanding / Owned Elsewhere

| Asset | Notes |
|-------|-------|
| **Vibe Code Calculator** | Rest of team is building this; not in this workstream |
| **Steering Committee Setup Guide** | Identified but not yet built |
| **CFO Defense Deck — merge** | 6 separate PPTX files need to be merged into one |
| **Hub integration** | All standalone files need to be stitched into a unified site — **this is the Claude Code workstream** |

---

## The Claude Code Integration Workstream

This is why you're here. Here's what needs to happen:

### 1. Unify the Design System
All tools were built with a shared aesthetic (dark background `#0d0d0d`, off-white text `#f0ede8`, gold `#C8A96E`, teal `#7EB8A4`, coral `#E07B5A`, DM Serif Display + DM Mono + DM Sans typography). The hub prototype sets the canonical design language. Normalize all standalone tools to match.

### 2. Wire Up Navigation
The hub's resource library cards should open/link to each tool. Some tools are designed as modals (the SOP modal has `<!-- MERGE START -->` and `<!-- MERGE END -->` comment markers for easy insertion). Others work better as full pages. Decision framework:
- **Modal:** Assets with a primary CTA of "download" (SOP, worksheet, hiring exercises)
- **Full page / section:** Interactive tools with their own state (calculator, diagnostic, API library, scheduler)

### 3. Integrate the Diagnostic as the Entry Point
The AI Mandate Diagnostic should fire on first visit to the hub (or be prominently in the hero). It's 5 questions, no friction, and drops users into the right phase. The hub CTA currently says something like "Find your starting point →" — wire this to the diagnostic.

### 4. Merge the CFO Deck
6 separate `.pptx` files → 1 unified deck. python-pptx or equivalent. Sections:
1. The Mandate (framing)
2. The Stakes (why this is hard)
3. The Framework (Tierney's five phases)
4. Build vs. Buy (slide from Section 5 was noted as strong)
5. Vendor Evaluation (Drew/Armanino insights)
6. The Ask (what you need from the CFO)

### 5. Host & Deploy
All files are standalone — no backend needed. Static hosting (Vercel, Netlify, or similar) is appropriate. All inter-tool links should be relative.

---

## Project File Locations

```
/mnt/project/
├── Transcript_-_Conversation_with_Drew_Armanino___Dean_Quiambao_of_Armanino
├── _Infinite_Work__by_David_Fuhriman
├── NigelNumericCallDeckv6.pdf          ← David's deck (NOT Nigel's)
└── AI_Mandate_Campaign.pdf

/mnt/user-data/outputs/
├── build-vs-buy-calculator.html
├── build-vs-buy-worksheet.docx
└── [all other deliverables]

/mnt/transcripts/
└── [interview transcripts — check journal.txt for index]
```

**Google Drive:** Transcripts also live in Google Drive. Search using `name contains '[filename]'` — more reliable than full-text search.

**FigJam board:** File key `pdcdm6bbApgcyenJk5JqS2` — design references and inspiration board. Node ID-based screenshot retrieval works reliably via Figma MCP.

---

## Important Context / Watch-Outs

- **`NigelNumericCallDeckv6.pdf`** is David Fuhriman's deck that he included in an email to Nigel about building a Numeric API. It is **not** something Nigel created. Don't misattribute it.
- **David's and Tierney's frameworks are additive, not competing.** David = organizational readiness. Tierney = operational sequencing. Present them as complementary.
- **The Build vs. Buy scoring weights:** Uniqueness (25%), Maintenance Capacity (20%), Defensibility Stakes (25%), Vendor Viability (15%), Cost of Failure (15%). These are a first pass — Nigel may want to pressure-test them.
- **Demo skepticism (Drew Armanino):** "Everything demos well." This is a recurring theme and intentionally surfaces in the Buy verdict copy of the calculator and the Buy zone of the worksheet. Don't flatten it.
- **The Hackathon Scheduler** is specifically informed by Drew's advice on implementation timelines (weeks, not months for AI-native tools) and Cindy's sprint methodology. It's not a one-time event tool — it's an ongoing cadence.

---

## Tone & Voice

Finance-grade. Authoritative but not stuffy. The audience is smart, under pressure, and deeply skeptical of AI hype. The playbook earns trust by being genuinely useful and not overselling.

Avoid: generic AI optimism, vague transformation language, anything that sounds like a vendor pitch.
Lean into: specificity, honest tradeoffs, the voice of practitioners (quotes from the interview subjects ground everything).

The editorial aesthetic (DM Serif Display headlines, DM Mono labels, dark backgrounds) signals seriousness. It should feel like something a Bloomberg Terminal user would trust.

---

## Questions to Ask Nigel Before Proceeding

1. Where are the final output files hosted / what's the deploy target?
2. Does the CFO Deck merge need to happen before or after hub integration?
3. Should the Steering Committee Setup Guide be built before integration, or can it be a stub with "coming soon"?
4. What's the canonical URL structure? (e.g. `/playbook`, `/playbook/calculator`, etc.)

---

*Built in Claude.ai claude.ai Projects across ~8 sessions, March 2026. All standalone assets validated and complete. Integration is the outstanding work.*
