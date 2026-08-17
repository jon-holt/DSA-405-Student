# P1: Framing a Data Problem

**DSA 405 · Fall 2026 · Project Milestone 1**

| | |
|---|---|
| **Introduced** | Week 1 (Aug 21). Prep: post three project ideas to the Week 2 forum. |
| **Due** | **Thursday, Sep 3, 11:59 PM** |
| **Weight** | 5% of course grade · scored on the P1 rubric, 4 criteria |
| **Submit** | Notebook to Moodle. Filename `DSA405_002_FA26_P1_[yourUnityID].ipynb` |
| **Time** | 2–3 hours across two weeks, most of it looking at candidate sources |

**Revision available once**, within a week of feedback.

---

## Purpose

P1 is the project plan: the question, the sources, and the declared difficulty, written
precisely enough that a reader could judge whether the plan will work.

Four components: a question, two named sources with evidence that each is reachable,
evidence that collection is permitted, and a tier declaration.

**The core requirement, from the syllabus:** answer a question using **at least two data
sources that must be combined**, where **at least one comes off the web** by scrape or
API. A pre-packaged Kaggle download does not satisfy the web-source requirement.

P1 is the cheapest milestone to redo. Redirecting a project in Week 4 costs nothing;
redirecting in Week 12 costs the grade. An hour spent examining candidate data now
prevents discovering in October that a source has 40 usable rows.

---

## Deliverables

Four sections, one notebook. Prose cells for the writing, code cells for the evidence.

### 1. The question

One sentence, answerable with data that can be named, plus a short paragraph on why it
matters to someone besides the grader and what an answer would change.

The test is topic versus question. "Restaurant inspections in Wake County" is a topic.
"Do chain restaurants in Wake County hold more stable inspection scores than
independents?" is a question: the table that would answer it can be described.

The question usually changes once the data is in hand; P4 asks for a description of that
shift. P1 grades whether a real question exists at all.

### 2. Sources & access evidence

**Two or more sources, at least one off the web.** For each one:

| | |
|---|---|
| Publisher | who produces and hosts it |
| URL | the actual page, not the site's front door |
| Coverage & time span | what it includes, over what period |
| Approximate size | rows, records, or pages, as a number |
| Access method | download / `read_html` / scrape / API |

Then **paste in evidence that each source is reachable**: a row count from `read_csv`
or `read_html` (the Week 2 Lab covers both), a status code, or a screenshot of the data
on screen. A screenshot requires no code, so no source is exempt.

Finish with one sentence naming the **likeliest failure point**: the least trusted
source, and the fallback if it falls through.

### 3. Constraints & guardrails

For each source, find and **quote** the constraint that applies to it:

- **Anything scraped:** the site's `robots.txt` (it lives at `site.com/robots.txt`; open
  it in a browser) and its terms of service. Week 8 covers reading these in detail; for
  P1, find them, quote the relevant line, and flag anything uncertain.
- **Downloads and APIs:** the license or terms of use, and any attribution they require.

Then certify the plan against the **course guardrails** (syllabus, *Project Guardrails*),
each one by name:

- Scrape only purpose-built sandboxes, sites with a documented API or open-data license,
  or sites whose robots.txt and terms of service permit it
- Never data behind a login or paywall
- Never personal or identifiable information about individuals
- Always rate-limit, identify the scraper honestly, and cache

If a site says no, that is the answer. A source ruled out with the terms quoted is good
P1 material, not a failure. When in doubt, ask the instructor before writing the
request.

### 4. Tier declaration

Declare a tier, with one sentence on why it fits the student and these sources.

| Tier | What it takes |
|---|---|
| **1 — Solid** | Two sources; one via `read_html` or a documented API. A one-to-one or one-to-many join. |
| **2 — Ambitious** | Two or more sources; one requiring a multi-page scrape with pagination, session handling, and rate limiting. |
| **3 — Stretch** | Tier 2, plus either structured extraction from unstructured text or PDF with a validated schema, or a third source requiring a many-to-many resolution. |

Tiers may be raised any time up to P3 and may not be lowered after P3. Tier affects
exactly one rubric row in the entire course: P4 Criterion 5, Technical Ambition. **Tier 1
executed cleanly lands in the A-minus range.** Declaring a tier accurately scores better
than declaring ambitiously and drifting.

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Question & motivation | ×1 | A real question, answerable with the stated data, that matters to someone |
| Sources & access evidence | ×2 | Named precisely, one off the web, reachability shown not asserted |
| Applicable constraints & guardrails | ×2 | The constraint that applies to each source, quoted; every guardrail certified |
| Tier declaration & fit | ×1 | A tier that matches the project described |

Full descriptors in *DSA 405 Project Rubrics*. Proficient across the board is an 88.

**Submit a self-scored copy of the rubric.** It is ungraded, takes about ten minutes,
and catches omissions before grading does.

---

## Common failure modes

**A topic instead of a question.** A Section 1 with no verb is a topic. Identify the
table or chart that would settle the question; if none can be described, keep
sharpening.

**Access asserted, not evidenced.** "The data is available on the county website" scores
2. A pasted row count scores 3. The difference is twenty minutes of work now versus a
dead project in October.

**The generic constraints paragraph.** "I will follow all applicable terms of service"
cites nothing and scores 2. Quote the line from the source's own robots.txt or license
that permits the planned collection.

---

## P1 Checklist

- [ ] One sentence stating the question, answerable with the named data
- [ ] Two or more sources, each with publisher, URL, coverage, and size
- [ ] At least one source comes off the web (scrape or API)
- [ ] Evidence each source is reachable, pasted in
- [ ] The constraint that applies to each source, quoted
- [ ] Every course guardrail addressed by name
- [ ] Tier declared, with one sentence on why
- [ ] Self-scored rubric attached
