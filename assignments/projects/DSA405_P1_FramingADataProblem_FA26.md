# P1: Framing a Data Problem

**DSA 405 · Fall 2026 · Project Milestone 1**

| | |
|---|---|
| **Introduced** | Week 1 (Aug 21). Prep: post three project ideas to the Week 2 forum. |
| **Due** | **Thursday, Sep 3, 11:59 PM** |
| **Weight** | 5% of course grade · scored on the P1 rubric, 4 criteria |
| **Submit** | Notebook to Moodle. Filename `DSA405_002_FA26_P1_[yourUnityID].ipynb` |
| **Time** | 2–3 hours across two weeks, most of it looking at candidate sources |

---

## Purpose

P1 is the project plan: the question, the sources, and the declared difficulty, written
precisely enough that a reader could judge whether the plan will work.

Four components: a question, two named sources with evidence that each is reachable,
evidence that collection is permitted, and a tier declaration.

**The core requirement:** answer a question using **at least two data
sources that must be combined**, where **at least one is collected from the web** by
scrape or API. To scrape is to collect data from web pages using a program you write;
an API is a service a site provides so that programs can request its data directly.
A pre-packaged Kaggle download does not satisfy the web-source requirement.

---

## Deliverables

Four sections, one notebook. Prose cells for the writing, code cells for the evidence.

### 1. The question

One sentence, answerable with data that can be named, plus a short paragraph on why it
matters to someone besides the grader and what an answer would change.

The test is whether you wrote a topic or a question. "Restaurant inspections in Wake County" is a topic.
"Do chain restaurants in Wake County have more stable inspection scores than
independents?" is a question: the table that would answer it can be described.

The question usually changes once you start working with the data; P4 asks you to
describe that change. P1 grades whether a real question exists at all.

### 2. Sources & access evidence

**Two or more sources, at least one collected from the web.** For each one:

| | |
|---|---|
| Publisher | who produces and hosts it |
| URL | the exact page where the data is, not the site's home page |
| Coverage & time span | what it includes, over what period |
| Approximate size | rows, records, or pages, as a number |
| Access method | download / `read_html` / scrape / API |

Then **paste in evidence that each source is reachable**: a row count from `read_csv`
or `read_html` (the Week 2 Lab covers both), a status code, or a screenshot of the data
on screen. A screenshot requires no code, so no source is exempt.

Finish with one sentence naming the **most likely point of failure**: which source you
trust least, and what backup source or plan you will use if that source turns out to be
unusable.

### 3. Constraints & guardrails

For each source, find and **quote** the constraint that applies to it:

- **Anything scraped:** the site's `robots.txt` and its terms of service. A
  `robots.txt` is a text file in which the site's owner states which pages automated
  programs may fetch; you can see it by opening `site.com/robots.txt` in a browser. Week 8
  covers reading these in detail; for P1, find them, quote the relevant line, and note
  anything you are unsure about.
- **Downloads and APIs:** the license or terms of use, and any attribution they require.

Then certify the plan against the **course guardrails**. The guardrails are the safety
rules every project in this course must follow:

- Scrape only purpose-built sandboxes (practice websites built to be scraped), sites
  with a documented API or open-data license, or sites whose robots.txt and terms of
  service permit it
- Never data behind a login or paywall
- Never personal or identifiable information about individuals
- Always rate-limit, identify the scraper honestly, and cache

If a site's robots.txt or terms of service forbid collection, that answer is final: we do
not collect from that site. A source you ruled out, with the forbidding terms quoted, is
good P1 material, not a failure. If you are unsure, ask the instructor before writing any
code that sends requests.

### 4. Tier declaration

Declare a tier, with one sentence on why it fits the student and these sources.

Some terms in this table (joins, pagination, schema) are taught in Weeks 6–12, after
P1 is due. You do not need to master them now; pick the tier that matches your plan,
and ask me if an unfamiliar term makes the choice unclear.

| Tier | What it requires |
|---|---|
| **1 — Solid** | Two sources; one via `read_html` or a documented API. A one-to-one or one-to-many join. |
| **2 — Ambitious** | Two or more sources; one requiring a multi-page scrape with pagination, session handling, and rate limiting. |
| **3 — Stretch** | Tier 2, plus either structured extraction from unstructured text or PDF with a validated schema, or a third source requiring a many-to-many resolution. |

Tiers may be raised any time up to P3 and may not be lowered after P3. Tier affects
exactly one rubric row in the entire course: P4 Criterion 5, Technical Ambition. 

---

## How this is graded

| Criterion | Wt | The short version |
|---|---|---|
| Question & motivation | ×1 | A real question, answerable with the stated data, that matters to someone |
| Sources & access evidence | ×2 | Named precisely, one collected from the web, with pasted evidence that each source is reachable |
| Applicable constraints & guardrails | ×2 | The constraint that applies to each source, quoted; every guardrail certified |
| Tier declaration & fit | ×1 | A tier that matches the project described |

Full descriptors in *DSA 405 Project Rubrics*.

**Submit a self-scored copy of the rubric.** It is ungraded, and it helps you notice missing pieces before we grade.

---

## Common failure modes

**A topic instead of a question.** A Section 1 with no verb is a topic. Identify the
table or chart that would answer the question. If you cannot describe one, the question
is not specific enough yet; keep revising it until you can.

**Access asserted, not evidenced.** "The data is available on the county website" is a
claim without evidence. A pasted row count is evidence. The difference is about twenty
minutes of work now, versus discovering in October that the data cannot actually be
collected, after weeks of project work already depend on it.

**The generic constraints paragraph.** "I will follow all applicable terms of service"
cites nothing. Quote the line from the source's own robots.txt or license
that permits the planned collection.

---

## P1 Checklist

- [ ] One sentence stating the question, answerable with the named data
- [ ] Two or more sources, each with publisher, URL, coverage, and size
- [ ] At least one source is collected from the web (scrape or API)
- [ ] Evidence each source is reachable, pasted in
- [ ] The constraint that applies to each source, quoted
- [ ] Every course guardrail addressed by name
- [ ] Tier declared, with one sentence on why
- [ ] Self-scored rubric attached
