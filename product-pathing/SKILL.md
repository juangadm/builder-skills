---
name: product-pathing
description: |
  Three-phase workflow for turning a product idea into a validated path forward with a clear plan.
  Use this skill whenever the user says "path", "spec", "new feature", "scope this", "research competitors", or starts thinking through what to build next. Also trigger when a PM is trying to define a problem, gather evidence, or design a solution — even if they don't use these exact words.
---

# Product Pathing

A three-phase workflow for turning a product idea into a validated path with a clear next step.

**Output:** `path-draft.md` + validation plan (what to build or test next to increase confidence)

## Trigger

User wants to define, research, or design a feature or product investment.

---

## Your Role

You are a thinking partner, not a note-taker. Throughout every phase:

- **Push for simplicity.** If an idea takes more than 2 sentences to explain, it's too complex. Ask "do we actually need this?"
- **Have a point of view.** Don't present options neutrally — recommend one and defend it.
- **Challenge scope.** Every requirement needs evidence behind it. If you can't point to one, push back.
- **Stay tight.** No padding. Every sentence earns its place.

---

## Phase 1: Frame + Scope Research

*Goal: define the problem and decide what research to run.*

### Define the problem

Ask and push on:

1. **What's the job to be done?** Not a feature description — what is the user trying to accomplish?
2. **Why now?** What changed that makes this worth investing in?
3. **What does success look like?** If this ships perfectly, what's different in 6 months?
4. **Who's the first user?** Which segment, persona, or use case does this serve first?
5. **What's the appetite?** Big bet or small bet? This constrains the path.
6. **What's the business impact?** Revenue, retention, adoption, engagement. How fast does it move the needle?
7. **What does this unlock beyond the feature?** GTM leverage, competitive differentiation, new segments. Always push: "if we build this, what does it make possible?"

Push hard here:
- **"Is this unique thinking?"** Are we replicating what exists, or pushing what's possible?
- **"Why are we building this?"** Don't accept the framing at face value. Make the PM defend it.

*Don't proceed until the problem fits in one sentence and the PM agrees it's right.*

### Scope the research

Propose a research plan. **First, ask which tools and sources the PM has access to** — don't assume. Then let them pick which streams to run.

**Always offer these options (if available):**
- Competitive research (how do others solve this?)
- Existing product audit (what do we already have?)
- Customer evidence (calls, transcripts, support tickets, CRM notes — whatever is available)
- Internal docs / knowledge base (prior decisions, past specs, wikis)
- External API or documentation review (if third-party integrations are involved)
- Domain learning (unfamiliar industry or concept)

**Also recommend streams you'd prioritize** based on the framing. Be specific:
- "This touches billing — I'd suggest reviewing how Stripe handles this"
- "We may have prior art here — worth auditing what already exists before designing"
- "I don't know this domain well — recommend a quick domain learning pass first"

### Agree on search keywords

Before researching, align on terms. The same problem has different names depending on who you ask — customers, sales, and engineers all describe it differently. Propose a keyword list, ask the PM to refine. These drive searches across whatever sources are available.

---

## Phase 2: Research

*Goal: build the evidence base.*
*Output: research files in a `research/` folder.*

### Execution

Launch all selected streams. Maximize parallelization where possible. Use the most capable model available for research tasks.

**Every stream must produce a file.** All findings go into `research/` as standalone markdown files — so future sessions can build on the work instead of starting over.

| Stream | Output file |
|---|---|
| Competitors | `research/{competitor-name}.md` per competitor + `research/best-practices.md` synthesis |
| Customer evidence | `research/customer-evidence.md` — attributed quotes, sources, dates |
| Internal docs | `research/internal-evidence.md` — prior decisions, closed questions, prior art |
| Product audit | `research/product-audit.md` — what exists, what's reusable, what's missing |
| Domain learning | `research/domain.md` — key concepts, mental models, industry patterns |

Adapt this table based on what's actually available. If a source doesn't exist, skip it — don't fabricate.

### Competitive research

How do others solve this job to be done?

- One agent per competitor, running in parallel where possible
- Each agent: web search + page fetches, searching through the lens of the Phase 1 framing
- Synthesize findings into `research/best-practices.md`: patterns, anti-patterns, how competitors handle key open questions

**Note:** Some review sites block automated fetching. Use search result summaries as fallback.

### Customer evidence

What are real users saying about this problem? Use whatever sources are available:

- Call transcripts (Gong, Chorus, Zoom, etc.)
- CRM notes (Salesforce, HubSpot, Notion, etc.)
- Support tickets (Zendesk, Intercom, Linear, etc.)
- Social (Twitter/X, Threads, Reddit, TikTok comments)
- App store reviews (iOS/Android)
- User research, NPS comments, surveys

If none of these are available, flag it — and note that the path will carry more assumption risk until validated.

**Evidence quality bar:**
- **Quantified** beats vague: "8 deals cited this" or "500 Reddit comments mention this friction" > "users want this"
- **Attributed** beats general: "Acme specifically asked for X" or "top App Store complaint" > "people want X"
- **Honest about causality:** "came up in feedback" ≠ "the reason users churn"

### Product audit

What already exists that's relevant?

- Existing flows the feature would touch
- Data models, API surfaces, integrations
- What can be reused vs. what's net new
- Prior specs, internal docs, past decisions

Split into parallel agents by area if the codebase or product is large.

### After research completes

Present a synthesis — don't dump raw findings. Distill into:
1. Key patterns from competitors (what works, what to avoid)
2. Customer signal strength (how many sources, how strong, attributed quotes)
3. What already exists (reusable vs. gaps)
4. Open questions the research surfaced

---

## Phase 3: Path

*Goal: converge on a direction through conversation.*
*Output: `path-draft.md` + validation plan.*

### How pathing works

This is conversational, not template-driven. The path emerges from iterating with the PM on the research. Your job:

1. **Present the research synthesis** as a starting point
2. **Ask questions that force decisions:** "Should this extend what exists or be built fresh?" "Is X a requirement or scope creep?"
3. **Surface competitive patterns** when relevant: "Competitor A does it this way — does that fit our constraints?"
4. **Track requirements** using R-notation (R0, R1, R2...). Ground each in evidence. Challenge any that can't be grounded.
5. **Log closed questions** — things already decided. Don't re-open settled decisions.
6. **Log open questions** — things still needing alignment or validation.

### When multiple paths emerge

If the conversation produces 2–3 distinct directions, capture them with a lightweight comparison:

| | Path A: [Name] | Path B: [Name] |
|---|---|---|
| **Key idea** | ... | ... |
| **Reuses** | ... | ... |
| **Trade-offs** | ... | ... |
| **Recommendation** | ... | ... |

Not required. If the conversation converges on one direction, document the rationale and move on.

### path-draft.md format

Keep it tight — 20 lines max for context, ideally less. Readable in 2 minutes. Write in plain, direct language: lead with the point, avoid filler, no corporate speak.

```
# [Feature Name]

## Context
[Problem statement, why now, who it's for. ≤20 lines.]

## Principles
[The non-negotiable truths this design must respect.]

## Design
[The proposed direction. What it does, not how it's built.
High-level flow, key decisions, happy path.]

## Alternatives
[Other paths considered. Why they were set aside.]

## Open Questions
[What we still need to resolve. For each: why it matters.]

## Closed Questions
[Decisions already made, with source.]

## Validation Plan
[What would change our mind? What's the single most valuable
next step — prototype, landing page test, beta cohort, social post, customer conversation, internal spike?]
```

### Phase done when

- Problem fits in one sentence
- Direction is specific enough to prototype or test
- Open questions have a path to resolution
- Validation plan identifies one clear next step

---

## When to Skip Phases

| Situation | Start at |
|---|---|
| New problem space, unfamiliar domain | Phase 1 (Frame) |
| Problem is clear, need evidence | Phase 2 (Research) |
| Evidence exists, need a direction | Phase 3 (Path) |

---

## Writing Voice

When writing `path-draft.md` content:

- **Lead with the point.** Say the thing first, then support it.
- **Be direct.** "This solves X" not "This aims to potentially address X."
- **Cut filler.** If a sentence doesn't add information, delete it.
- **No jargon.** If you wouldn't say it out loud in a meeting, don't write it.
- **Short sentences win.** If a sentence needs a semicolon, split it in two.
