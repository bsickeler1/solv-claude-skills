---
name: monarch-deal-analysis
description: Analyze and report on Project Monarch prospect deals for leadership. Use this skill whenever the user asks about Monarch deals, prospect status, deal pipeline, deal summaries, leadership updates, or asks to "pull together" or "update" deals. Pulls context from Slack (#mon-prosp-* channels), Granola meeting notes, and Gong calls, then produces two outputs: (1) a tight per-deal bullet summary under 300 words, and (2) a leadership-ready table that fits on one slide. Trigger this whenever the user mentions "Monarch", "monarch deals", "deal update", "pipeline summary", or asks for a leadership-ready status on prospects.
---

# Project Monarch Deal Analyzer

You are pulling together a leadership-ready update on one or more Project Monarch prospect deals. The goal is crisp, high-signal output — not a brain dump. Leadership needs to quickly understand where each deal stands and what matters.

## Data Sources (pull in this order)

For each deal, gather context from:

1. **Slack** — search for `#mon-prosp-<PROSPECTNAME>` (e.g., `#mon-prosp-cls`, `#mon-prosp-gloc`). Read the most recent 20-30 messages. Look for pricing discussions, objections, next steps, stakeholder names, blockers.
2. **Granola** — search meeting notes for the prospect name. Pull the 2-3 most recent meetings. Focus on: what was decided, what's blocking, what the prospect said about timing/concerns.
3. **Gong** — if available via browser or Salesforce, pull the latest call summary for the prospect. Look for tone signals, open objections, champion strength.

If a source has no data for a deal, note it and move on — don't block on it.

## Deals to Analyze

Only include deals that are Monarch deals — identified by "Monarch" in the opportunity name in Salesforce (e.g., "Great Lakes Orthopaedic Center - Monarch"), a `#mon-prosp-*` Slack channel, or explicit mention of Monarch in meeting notes. Exclude deals for other Solv products (OS, Reg, ClearPay standalone, etc.) unless they are part of a Monarch bundle.

If the user specifies a deal or list of deals, analyze those. If they say "all" or "pipeline", analyze all active Monarch prospects you can find data for (exclude Closed Lost).

## Deal Metadata to Track

Extract these fields for each deal:

- **Deal Type**: New Logo | Expansion | Design Partner | Renewal (infer from context)
- **Size**: Monthly or annual contract value if mentioned, or location/visit volume as a proxy (e.g., "2 clinics, ~700 calls/week")
- **EHR**: The prospect's EMR/EHR system (e.g., ECW, Epic, Athena, Veradigm)
- **Deal Phase**: Use Solv sales stages — Prospecting → Clear Pain & Criteria → Building Our Champion → Clear MSP → Paper Process → Closed Won
- **Key Notes**: The single most important thing leadership needs to know right now (pricing objection, executive sponsor, timeline, blocker)

## Output Format

Produce BOTH outputs every time.

---

### Output 1: Per-Deal Executive Summaries

One section per deal. Format:

**[Prospect Name]** — [Deal Phase] | [Deal Type]
- **Size**: [value or proxy]
- **EHR**: [system]
- **Champion**: [name/title if known]
- **Status**: 2-3 sentence max narrative — where things stand, what happened last
- **Key risks**: 1-3 bullets, each under 15 words
- **Next step**: One clear action with owner and timing if known

Hard limit: 300 words per deal. Cut anything that doesn't change a decision.

---

### Output 2: Leadership Table (One-Slide Ready)

After all per-deal summaries, output this table:

| Prospect | Deal Type | Size | EHR | Deal Phase | Key Notes |
|----------|-----------|------|-----|------------|-----------|

- Keep Key Notes to one tight sentence (under 20 words)
- Order rows by deal phase (most advanced first)
- If a field is unknown, write "—" not "N/A" or "Unknown"

---

## Tone and Style

- Write like you're briefing a VP with 90 seconds — direct, no padding
- Flag risks explicitly, don't soften them
- Use present tense ("CLS is pushing back on pricing" not "CLS was pushing back")
- If you're inferring something (e.g., deal type not explicitly stated), note it briefly with "(inferred)"

## When Data Is Sparse

If you can only find one source for a deal, note it at the top of that deal's summary: "Note: based on Granola only — no Slack or Gong data found." Still produce both outputs with what you have.
